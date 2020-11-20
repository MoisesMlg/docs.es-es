---
title: 'dotnet-counters: .Net Core'
description: Obtenga información sobre cómo instalar y usar la herramienta de línea de comandos dotnet-counter.
ms.date: 02/26/2020
ms.openlocfilehash: 7ff29ad91ad271afd35e3d38a4d748bc79ad6c03
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507259"
---
# <a name="dotnet-counters"></a><span data-ttu-id="ba47f-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="ba47f-103">dotnet-counters</span></span>

<span data-ttu-id="ba47f-104">**Este artículo se aplica a:** ✔️ SDK de .NET Core 3.0 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="ba47f-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="ba47f-105">Instalación de dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="ba47f-105">Install dotnet-counters</span></span>

<span data-ttu-id="ba47f-106">Para instalar la versión de lanzamiento más reciente del [paquete NuGet](https://www.nuget.org/packages/dotnet-counters) de `dotnet-counters`, use el comando [dotnet tool install](../tools/dotnet-tool-install.md):</span><span class="sxs-lookup"><span data-stu-id="ba47f-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="ba47f-107">Sinopsis</span><span class="sxs-lookup"><span data-stu-id="ba47f-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="ba47f-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="ba47f-108">Description</span></span>

<span data-ttu-id="ba47f-109">`dotnet-counters` es una herramienta de supervisión de rendimiento diseñada para la investigación del rendimiento y la supervisión del estado de primer nivel ad hoc.</span><span class="sxs-lookup"><span data-stu-id="ba47f-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="ba47f-110">Puede observar los valores del contador de rendimiento que se publican a través de la API <xref:System.Diagnostics.Tracing.EventCounter>.</span><span class="sxs-lookup"><span data-stu-id="ba47f-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="ba47f-111">Por ejemplo, se pueden supervisar rápidamente cosas como el uso de la CPU o la velocidad de las excepciones que se producen en la aplicación .NET Core para ver si hay algo sospechoso antes de profundizar en una investigación de rendimiento más seria mediante `PerfView` o `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="ba47f-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="ba47f-112">Opciones</span><span class="sxs-lookup"><span data-stu-id="ba47f-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="ba47f-113">Muestra la versión de la utilidad dotnet-counters.</span><span class="sxs-lookup"><span data-stu-id="ba47f-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ba47f-114">Muestra la ayuda de la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="ba47f-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="ba47f-115">Comandos</span><span class="sxs-lookup"><span data-stu-id="ba47f-115">Commands</span></span>

| <span data-ttu-id="ba47f-116">Comando</span><span class="sxs-lookup"><span data-stu-id="ba47f-116">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="ba47f-117">dotnet-counters collect</span><span class="sxs-lookup"><span data-stu-id="ba47f-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="ba47f-118">dotnet-counters list</span><span class="sxs-lookup"><span data-stu-id="ba47f-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="ba47f-119">dotnet-counters monitor</span><span class="sxs-lookup"><span data-stu-id="ba47f-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="ba47f-120">dotnet-counters ps</span><span class="sxs-lookup"><span data-stu-id="ba47f-120">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="ba47f-121">dotnet-counters collect</span><span class="sxs-lookup"><span data-stu-id="ba47f-121">dotnet-counters collect</span></span>

<span data-ttu-id="ba47f-122">Recopila periódicamente los valores de contador seleccionados y los exporta a un formato de archivo especificado para su posterior procesamiento.</span><span class="sxs-lookup"><span data-stu-id="ba47f-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="ba47f-123">Sinopsis</span><span class="sxs-lookup"><span data-stu-id="ba47f-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="ba47f-124">Opciones</span><span class="sxs-lookup"><span data-stu-id="ba47f-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="ba47f-125">Id. del proceso que se va a supervisar.</span><span class="sxs-lookup"><span data-stu-id="ba47f-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="ba47f-126">Número de segundos de retraso entre la actualización de los contadores mostrados.</span><span class="sxs-lookup"><span data-stu-id="ba47f-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="ba47f-127">Una lista de contadores separados por comas.</span><span class="sxs-lookup"><span data-stu-id="ba47f-127">A comma-separated list of counters.</span></span> <span data-ttu-id="ba47f-128">Los contadores pueden ser `provider_name[:counter_name]` especificados.</span><span class="sxs-lookup"><span data-stu-id="ba47f-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="ba47f-129">Si se usa `provider_name` sin una lista de contadores que cumplan los requisitos, se mostrarán todos los contadores del proveedor.</span><span class="sxs-lookup"><span data-stu-id="ba47f-129">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="ba47f-130">Para descubrir los nombres del proveedor y del contador, use el comando [dotnet-counters list](#dotnet-counters-list).</span><span class="sxs-lookup"><span data-stu-id="ba47f-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="ba47f-131">Formato que se va a exportar.</span><span class="sxs-lookup"><span data-stu-id="ba47f-131">The format to be exported.</span></span> <span data-ttu-id="ba47f-132">Actualmente disponibles: csv, json.</span><span class="sxs-lookup"><span data-stu-id="ba47f-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="ba47f-133">Nombre del archivo de salida.</span><span class="sxs-lookup"><span data-stu-id="ba47f-133">The name of the output file.</span></span>

- <span data-ttu-id="ba47f-134">**`-- <command>` (solo para seleccionar como destino aplicaciones que ejecutan .NET 5.0 o versiones posteriores)**</span><span class="sxs-lookup"><span data-stu-id="ba47f-134">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="ba47f-135">Después de los parámetros de configuración de la colección, el usuario puede anexar `--` seguido de un comando para iniciar una aplicación de .NET con un entorno de ejecución de 5.0 como mínimo.</span><span class="sxs-lookup"><span data-stu-id="ba47f-135">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="ba47f-136">`dotnet-counters` iniciará un proceso con el comando proporcionado y recopilará las métricas solicitadas.</span><span class="sxs-lookup"><span data-stu-id="ba47f-136">`dotnet-counters` will launch a process with the provided command and collect the requested metrics.</span></span> <span data-ttu-id="ba47f-137">Esto suele ser útil para recopilar métricas de la ruta de acceso de inicio de la aplicación y se puede usar para diagnosticar o supervisar los problemas que se producen antes o poco después del punto de entrada principal.</span><span class="sxs-lookup"><span data-stu-id="ba47f-137">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

> [!NOTE]
> <span data-ttu-id="ba47f-138">El uso de esta opción supervisa el primer proceso de .NET 5.0 que se comunica con la herramienta, lo que significa que, si el comando inicia varias aplicaciones de .NET, solo recopilará la primera.</span><span class="sxs-lookup"><span data-stu-id="ba47f-138">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="ba47f-139">Por tanto, se recomienda usar esta opción en aplicaciones independientes, o bien utilizar la opción `dotnet exec <app.dll>`.</span><span class="sxs-lookup"><span data-stu-id="ba47f-139">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

### <a name="examples"></a><span data-ttu-id="ba47f-140">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="ba47f-140">Examples</span></span>

- <span data-ttu-id="ba47f-141">Recopilación de todos los contadores en un intervalo de actualización de tres segundos y generación de un archivo CSV como salida:</span><span class="sxs-lookup"><span data-stu-id="ba47f-141">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- <span data-ttu-id="ba47f-142">Inicie `dotnet mvc.dll` como un proceso secundario y comience a recopilar contadores de tiempo de ejecución y contadores de hospedaje de ASP.NET Core del inicio, y guárdelo como una salida JSON:</span><span class="sxs-lookup"><span data-stu-id="ba47f-142">Start `dotnet mvc.dll` as a child process and start collecting runtime counters and ASP.NET Core Hosting counters from startup and save it as a JSON output:</span></span>

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="ba47f-143">dotnet-counters list</span><span class="sxs-lookup"><span data-stu-id="ba47f-143">dotnet-counters list</span></span>

<span data-ttu-id="ba47f-144">Muestra una lista de nombres y descripciones de contador, agrupada por proveedor.</span><span class="sxs-lookup"><span data-stu-id="ba47f-144">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="ba47f-145">Sinopsis</span><span class="sxs-lookup"><span data-stu-id="ba47f-145">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="ba47f-146">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ba47f-146">Example</span></span>

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs / min
    gen-1-gc-count                               Number of Gen 1 GCs / min
    gen-2-gc-count                               Number of Gen 2 GCs / min
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions / sec
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> <span data-ttu-id="ba47f-147">Los contadores de `Microsoft.AspNetCore.Hosting` se muestran cuando hay procesos identificados que admiten estos contadores, por ejemplo, cuando una aplicación ASP.NET Core se está ejecutando en el equipo host.</span><span class="sxs-lookup"><span data-stu-id="ba47f-147">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="ba47f-148">dotnet-counters monitor</span><span class="sxs-lookup"><span data-stu-id="ba47f-148">dotnet-counters monitor</span></span>

<span data-ttu-id="ba47f-149">Muestra la actualización periódica de los valores de los contadores seleccionados.</span><span class="sxs-lookup"><span data-stu-id="ba47f-149">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="ba47f-150">Sinopsis</span><span class="sxs-lookup"><span data-stu-id="ba47f-150">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [--counters] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="ba47f-151">Opciones</span><span class="sxs-lookup"><span data-stu-id="ba47f-151">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="ba47f-152">Id. del proceso que se va a supervisar.</span><span class="sxs-lookup"><span data-stu-id="ba47f-152">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="ba47f-153">Número de segundos de retraso entre la actualización de los contadores mostrados.</span><span class="sxs-lookup"><span data-stu-id="ba47f-153">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="ba47f-154">Una lista de contadores separados por comas.</span><span class="sxs-lookup"><span data-stu-id="ba47f-154">A comma-separated list of counters.</span></span> <span data-ttu-id="ba47f-155">Los contadores pueden ser `provider_name[:counter_name]` especificados.</span><span class="sxs-lookup"><span data-stu-id="ba47f-155">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="ba47f-156">Si se usa `provider_name` sin una lista de contadores que cumplan los requisitos, se mostrarán todos los contadores del proveedor.</span><span class="sxs-lookup"><span data-stu-id="ba47f-156">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="ba47f-157">Para descubrir los nombres del proveedor y del contador, use el comando [dotnet-counters list](#dotnet-counters-list).</span><span class="sxs-lookup"><span data-stu-id="ba47f-157">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

 <span data-ttu-id="ba47f-158">**`-- <command>` (solo para seleccionar como destino aplicaciones que ejecutan .NET 5.0 o versiones posteriores)**</span><span class="sxs-lookup"><span data-stu-id="ba47f-158">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="ba47f-159">Después de los parámetros de configuración de la colección, el usuario puede anexar `--` seguido de un comando para iniciar una aplicación de .NET con un entorno de ejecución de 5.0 como mínimo.</span><span class="sxs-lookup"><span data-stu-id="ba47f-159">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="ba47f-160">`dotnet-counters` iniciará un proceso con el comando proporcionado y supervisará las métricas solicitadas.</span><span class="sxs-lookup"><span data-stu-id="ba47f-160">`dotnet-counters` will launch a process with the provided command and monitor the requested metrics.</span></span> <span data-ttu-id="ba47f-161">Esto suele ser útil para recopilar métricas de la ruta de acceso de inicio de la aplicación y se puede usar para diagnosticar o supervisar los problemas que se producen antes o poco después del punto de entrada principal.</span><span class="sxs-lookup"><span data-stu-id="ba47f-161">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="ba47f-162">El uso de esta opción supervisa el primer proceso de .NET 5.0 que se comunica con la herramienta, lo que significa que, si el comando inicia varias aplicaciones de .NET, solo recopilará la primera.</span><span class="sxs-lookup"><span data-stu-id="ba47f-162">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="ba47f-163">Por tanto, se recomienda usar esta opción en aplicaciones independientes, o bien utilizar la opción `dotnet exec <app.dll>`.</span><span class="sxs-lookup"><span data-stu-id="ba47f-163">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

### <a name="examples"></a><span data-ttu-id="ba47f-164">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="ba47f-164">Examples</span></span>

- <span data-ttu-id="ba47f-165">Supervisión de todos los contadores de `System.Runtime` con un intervalo de actualización de 3 segundos:</span><span class="sxs-lookup"><span data-stu-id="ba47f-165">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 --counters System.Runtime
  Press p to pause, r to resume, q to quit.
      Status: Running

  [System.Runtime]
      % Time in GC since last GC (%)                                 0
      Allocation Rate (B / 1 sec)                                5,376
      CPU Usage (%)                                                  0
      Exception Count (Count / 1 sec)                                0
      GC Fragmentation (%)                                          48.467
      GC Heap Size (MB)                                              0
      Gen 0 GC Count (Count / 1 sec)                                 1
      Gen 0 Size (B)                                                24
      Gen 1 GC Count (Count / 1 sec)                                 1
      Gen 1 Size (B)                                                24
      Gen 2 GC Count (Count / 1 sec)                                 1
      Gen 2 Size (B)                                           272,000
      IL Bytes Jitted (B)                                       19,449
      LOH Size (B)                                              19,640
      Monitor Lock Contention Count (Count / 1 sec)                  0
      Number of Active Timers                                        0
      Number of Assemblies Loaded                                    7
      Number of Methods Jitted                                     166
      POH (Pinned Object Heap) Size (B)                             24
      ThreadPool Completed Work Item Count (Count / 1 sec)           0
      ThreadPool Queue Length                                        0
      ThreadPool Thread Count                                        2
      Working Set (MB)                                              19
  ```

- <span data-ttu-id="ba47f-166">Supervisión de únicamente el uso de la CPU y el tamaño del montón de GC de `System.Runtime`:</span><span class="sxs-lookup"><span data-stu-id="ba47f-166">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="ba47f-167">Supervisión de los valores `EventCounter` del elemento `EventSource` definido por el usuario.</span><span class="sxs-lookup"><span data-stu-id="ba47f-167">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="ba47f-168">Para obtener más información, consulte [Tutorial: Medición del rendimiento mediante EventCounters en .NET Core](event-counter-perf.md).</span><span class="sxs-lookup"><span data-stu-id="ba47f-168">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- <span data-ttu-id="ba47f-169">Inicie `my-aspnet-server.exe` y supervise el número de ensamblados cargados desde su inicio (solo para .NET 5.0 o versiones posteriores):</span><span class="sxs-lookup"><span data-stu-id="ba47f-169">Launch `my-aspnet-server.exe` and monitor the # of assemblies loaded from its startup (.NET 5.0 or later only):</span></span>

  <span data-ttu-id="ba47f-170">NOTA: Esto solo funciona para las aplicaciones que ejecutan .NET 5.0 o una versión posterior.</span><span class="sxs-lookup"><span data-stu-id="ba47f-170">NOTE: This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- <span data-ttu-id="ba47f-171">Inicie `my-aspnet-server.exe` con `arg1` y `arg2` como argumentos de la línea de comandos y supervise su espacio de trabajo y el tamaño del montón de GC desde su inicio (solo para .NET 5.0 o versiones posteriores):</span><span class="sxs-lookup"><span data-stu-id="ba47f-171">Launch `my-aspnet-server.exe` with `arg1` and `arg2` as command-line arguments and monitor its working set and GC heap size from its startup (.NET 5.0 or later only):</span></span>

  <span data-ttu-id="ba47f-172">NOTA: Esto solo funciona para las aplicaciones que ejecutan .NET 5.0 o una versión posterior.</span><span class="sxs-lookup"><span data-stu-id="ba47f-172">NOTE: This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[working-set,gc-heap-size] -- my-aspnet-server.exe arg1 arg2
  ```

  ```console
  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      GC Heap Size (MB)                                 39
      Working Set (MB)                                  59
  ```

## <a name="dotnet-counters-ps"></a><span data-ttu-id="ba47f-173">dotnet-counters ps</span><span class="sxs-lookup"><span data-stu-id="ba47f-173">dotnet-counters ps</span></span>

<span data-ttu-id="ba47f-174">Muestra una lista de los procesos de dotnet que se pueden supervisar.</span><span class="sxs-lookup"><span data-stu-id="ba47f-174">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="ba47f-175">Sinopsis</span><span class="sxs-lookup"><span data-stu-id="ba47f-175">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="ba47f-176">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ba47f-176">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
