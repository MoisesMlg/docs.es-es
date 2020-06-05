---
title: Depuración de una aplicación de consola de .NET Core con Visual Studio Code
description: Aprenda a depurar una aplicación de consola de .NET Core con Visual Studio Code.
ms.date: 05/26/2020
ms.openlocfilehash: eaeb97f54442006d2f0e29483a68dc3de89b5778
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202494"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-code"></a>Tutorial: Depuración de una aplicación de consola de .NET Core con Visual Studio Code

En este tutorial se presentan las herramientas de depuración disponibles en Visual Studio Code para trabajar con aplicaciones de .NET Core.

## <a name="prerequisites"></a>Requisitos previos

- Este tutorial funciona con la aplicación de consola que se crea en [Creación de una aplicación de consola de .NET Core en Visual Studio Code](with-visual-studio-code.md).

## <a name="use-debug-build-configuration"></a>Uso de la configuración de compilación de depuración

*Depuración* y *Versión* son dos de las configuraciones de compilación de .NET Core. Use la configuración de compilación Depuración para depurar y la configuración de compilación Versión para la distribución final de la versión.

En la configuración de depuración, el programa se compila sin optimizar y con toda la información de depuración simbólica. La optimización complica la depuración, ya que la relación entre el código fuente y las instrucciones generadas es más compleja. La configuración de versión del programa no contiene información de depuración simbólica y está totalmente optimizada.

 De forma predeterminada, Visual Studio Code usa la configuración de compilación Depuración, por lo que no es necesario cambiarla antes de depurar.

## <a name="set-a-breakpoint"></a>Establecer un punto de interrupción

Un punto de interrupción interrumpe temporalmente la ejecución de la aplicación *antes* de que se ejecute la línea con el punto de interrupción.

1. En *Program.cs*, establezca un *punto de interrupción* en la línea que muestre el nombre, la fecha y la hora; para ello, haga clic en el margen izquierdo de la ventana de código. El margen izquierdo está a la izquierda de los números de línea. Otra manera de establecer un punto de interrupción es colocar el cursor en la línea de código y luego presionar <kbd>F9</kbd>.

   En esta imagen vemos que Visual Studio Code marca la línea donde se establece el punto de interrupción con un punto rojo en el margen izquierdo.

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="Punto de interrupción":::

## <a name="set-up-for-terminal-input"></a>Configuración para la entrada de terminal

El punto de interrupción se encuentra después de una llamada al método `Console.ReadLine`. La **Consola de depuración** no acepta la entrada de terminal para un programa en ejecución. Para controlar la entrada de terminal durante la depuración, puede usar el terminal integrado (una de las ventanas de Visual Studio Code) o un terminal externo. En este tutorial, usará el terminal integrado.

1. Abra *.vscode/launch.json*.

1. Cambie la opción `console` a `integratedTerminal`.

   De:

   ```
   "console": "internalConsole",
   ```

   A:

   ```
   "console": "integratedTerminal",
   ```

1. Guarde los cambios.

## <a name="start-debugging"></a>Iniciar depuración

1. Abra la vista Depurar mediante el icono de depuración que hay en el menú de la izquierda.

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="Abrir la pestaña Depurar en Visual Studio Code":::

1. Para empezar la depuración, seleccione la flecha verde en la parte superior del panel, junto a **.NET Core Launch (console)** [Inicio de .NET Core (consola)].  Otra manera de empezar la depuración es presionar <kbd>F5</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="Empezar la depuración":::

1. Seleccione la pestaña **Terminal** para ver el mensaje "What is your name?" que muestra el programa antes de esperar una respuesta.

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="Seleccionar la pestaña Terminal":::

1. Escriba una cadena en la ventana **Terminal** para responder a la pregunta del nombre y presione <kbd>Entrar</kbd>.

   La ejecución del programa se detiene cuando llega al punto de interrupción y antes de que se ejecute el método `Console.WriteLine`. La sección **Variables locales** de la ventana **Variables** muestra los valores de las variables definidas en el método que se ejecuta actualmente.

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="Punto de interrupción alcanzado donde se muestran las variables locales":::

## <a name="change-variable-values"></a>Cambiar los valores de las variables

La ventana **Consola de depuración** permite interactuar con la aplicación que está depurando. Puede cambiar el valor de las variables para ver cómo afecta esto a su programa.

1. Seleccione la pestaña **Consola de depuración**.

1. Escriba `name = "Gracie"` en el símbolo del sistema de la parte inferior de la ventana **Consola de depuración** y presione la tecla <kbd>Entrar</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="Cambiar los valores de las variables":::

1. Escriba `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` en la parte inferior de la ventana **Consola de depuración** y presione la tecla <kbd>Entrar</kbd>.

   La ventana **Variables** muestra los nuevos valores de las variables `name` y `date`.

1. Para continuar con la ejecución del programa, seleccione el botón **Continuar** en la barra de herramientas. Otra manera de continuar es presionar <kbd>F5</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="Continuar la depuración":::

1. Seleccione de nuevo la pestaña **Terminal**.

   Los valores mostrados en la ventana de la consola corresponden a los cambios realizados en **Consola de depuración**.

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="Terminal que muestra los valores especificados":::

1. Presione cualquier tecla para salir de la aplicación y detenga la depuración.

## <a name="set-a-conditional-breakpoint"></a>Establecimiento de un punto de interrupción condicional

El programa muestra la cadena que escribe el usuario. ¿Qué sucede si el usuario no escribe nada? Puede probarlo con una característica de depuración muy útil denominada *Punto de interrupción condicional*.

1. Haga clic con el botón derecho (<kbd>Ctrl</kbd> + clic en macOS) sobre el punto rojo que representa al punto de interrupción. En el menú contextual, seleccione **Editar punto de interrupción** y se abrirá un cuadro de diálogo donde podrá escribir una expresión condicional.

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="Menú contextual del punto de interrupción":::

1. Seleccione `Expression` en el menú desplegable, escriba esta expresión condicional y presione <kbd>Entrar</kbd>.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="Escribir una expresión condicional":::

   Cada vez que se alcanza el punto de interrupción, el depurador llama al método `String.IsNullOrEmpty(name)` y se interrumpe en esta línea solo si la llamada al método devuelve `true`.

   En lugar de una expresión condicional, puede especificar un *número de llamadas*, que es lo que interrumpe la ejecución antes de que una instrucción se ejecute un número especificado de veces; o una *condición de filtro*, que es lo que interrumpe la ejecución del programa en función de atributos, como un identificador de subproceso, un nombre de proceso o un nombre de subproceso.

1. Inicie el programa con la depuración presionando <kbd>F5</kbd>.

1. En la ventana <kbd>Terminal</kbd>, cuando se le pida que escriba su nombre, presione la tecla **Entrar**.

   Como la condición que especificó (`name` es `null` o <xref:System.String.Empty?displayProperty=nameWithType>) se ha cumplido, la ejecución del programa se detiene cuando se alcanza el punto de interrupción y antes de que se ejecute el método `Console.WriteLine`.

   La ventana **Variables** muestra que el valor de la variable `name` es `""` o <xref:System.String.Empty?displayProperty=nameWithType>.

1. Confirme que el valor es una cadena vacía; para ello, escriba esta instrucción en la ventana **Consola de depuración** y presionando <kbd>Entrar</kbd>. El resultado es `true`.

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="La Consola de depuración devuelve un valor True después de ejecutar la instrucción":::

1. Seleccione el botón **Continuar** en la barra de herramientas para continuar la ejecución del programa.

1. Seleccione la pestaña **Terminal** y presione cualquier tecla para salir del programa y detener la depuración.

1. Para borrar el punto de interrupción, haga clic en el punto en el margen izquierdo de la ventana de código. Otra manera de borrar un punto de interrupción consiste en presionar <kbd>F9</kbd> mientras la línea de código está seleccionada.

1. Si recibe una advertencia que indica que se perderá la condición del punto de interrupción, seleccione **Quitar punto de interrupción**.

## <a name="step-through-a-program"></a>Ejecución paso a paso de un programa

Visual Studio Code también permite recorrer línea a línea un programa y supervisar su ejecución. Normalmente, establecería un punto de interrupción y seguiría el flujo del programa mediante una pequeña parte de su código de programa. Como este programa es pequeño, puede ejecutar paso a paso el programa entero.

1. Establezca un punto de interrupción en la llave de apertura del método `Main`.

1. Presiona <kbd>F5</kbd> para iniciar la depuración.

   Visual Studio Code resalta la línea del punto de interrupción.

   En este punto, la ventana **Variables** muestra que la matriz `args` está vacía, y `name` y `date` tienen valores predeterminados.

1. Seleccione **Depurar paso a paso por instrucciones** o presione <kbd>F11</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="Botón de depurar paso a paso por instrucciones":::

   Visual Studio Code resalta la línea siguiente.

1. Seleccione **Depurar paso a paso por instrucciones** o presione <kbd>F11</kbd>.

   Visual Studio Code ejecuta `Console.WriteLine` para el mensaje de nombre y resalta la siguiente línea de ejecución. La línea siguiente es `Console.ReadLine` para `name`. La ventana **Variables** no cambia y la pestaña **Terminal** muestra el mensaje "What is your name?".

1. Seleccione **Depurar paso a paso por instrucciones** o presione <kbd>F11</kbd>.

   Visual Studio resalta la asignación de la variable `name`. La ventana **Variables** muestra que `name` todavía es `null`.

1. Para responder al mensaje, escriba una cadena en la ventana Terminal y presione <kbd>Entrar</kbd>.

   Es posible que la pestaña **Terminal** no muestre la cadena mientras la está escribiendo, pero el método <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> capturará la entrada.

1. Seleccione **Depurar paso a paso por instrucciones** o presione <kbd>F11</kbd>.

   Visual Studio Code resalta la asignación de la variable `date`. La ventana **Variables** muestra el valor devuelto por la llamada al método <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. En la pestaña **Terminal** se muestra la cadena que escribió en el símbolo del sistema.

1. Seleccione **Depurar paso a paso por instrucciones** o presione <kbd>F11</kbd>.

   La ventana **Variables** muestra el valor de la variable `date` tras la asignación desde la propiedad <xref:System.DateTime.Now?displayProperty=nameWithType>.

1. Seleccione **Depurar paso a paso por instrucciones** o presione <kbd>F11</kbd>.

   Visual Studio Code llama al método <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. La ventana de la consola muestra la cadena con formato.

1. Seleccione **Depurar paso a paso para salir** o presione <kbd>Mayús</kbd>+<kbd>F11</kbd>.

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="Botón de depurar paso a paso para salir":::

1. Seleccione la pestaña **Terminal**.

   El terminal muestra "Presione cualquier tecla para salir..."

1. Presione cualquier tecla para salir de la aplicación.

## <a name="select-release-build-configuration"></a>Seleccionar Configuración de compilación de versión

Una vez que ha probado la versión de depuración de la aplicación, también debe compilar y probar la versión de lanzamiento. La versión de lanzamiento incorpora optimizaciones del compilador que pueden afectar al comportamiento de una aplicación. Por ejemplo, las optimizaciones del compilador que están diseñadas para mejorar el rendimiento pueden crear condiciones de carrera en aplicaciones multiproceso.

Para compilar y probar la versión de lanzamiento de la aplicación de consola, abra el **Terminal** y ejecute este comando:

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a>Recursos adicionales

* [Debugging in Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging) (Depuración en Visual Studio Code)

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha usado las herramientas de depuración de Visual Studio Code. Para descubrir cómo publicar una versión de la aplicación que se pueda implementar, vea [Publicar la aplicación](cli-create-console-app.md#publish-your-app).

<!--In the next tutorial, you publish a deployable version of the app.

> [!div class="nextstepaction"]
> [Publish a .NET Core console application with Visual Studio Code](publishing-with-visual-studio-code.md)
-->