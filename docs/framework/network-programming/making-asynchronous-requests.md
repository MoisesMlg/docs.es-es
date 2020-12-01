---
title: Realizar solicitudes asincrónicas
description: Obtenga información sobre cómo usan las clases System.Net el modelo de programación asincrónica estándar de .NET Framework para obtener acceso asincrónico a recursos de Internet.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, asynchronous access
- Networking
- asynchronous requests, Internet resources
- Network Resources
- WebRequest class, asynchronous access
ms.assetid: 735d3fce-f80c-437f-b02c-5c47f5739674
ms.openlocfilehash: f6eba7a1f10e037f93b20c0e7016f083e3e24200
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258717"
---
# <a name="making-asynchronous-requests"></a><span data-ttu-id="a5a70-103">Realizar solicitudes asincrónicas</span><span class="sxs-lookup"><span data-stu-id="a5a70-103">Making Asynchronous Requests</span></span>

<span data-ttu-id="a5a70-104">Las clases <xref:System.Net> usan el modelo de programación asincrónica estándar de .NET Framework para obtener acceso asincrónico a recursos de Internet.</span><span class="sxs-lookup"><span data-stu-id="a5a70-104">The <xref:System.Net> classes use the .NET Framework's standard asynchronous programming model for asynchronous access to Internet resources.</span></span> <span data-ttu-id="a5a70-105">Los métodos <xref:System.Net.WebRequest.BeginGetResponse%2A> y <xref:System.Net.WebRequest.EndGetResponse%2A> de la clase <xref:System.Net.WebRequest> inician y completan las solicitudes asincrónicas para un recurso de Internet.</span><span class="sxs-lookup"><span data-stu-id="a5a70-105">The <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods of the <xref:System.Net.WebRequest> class start and complete asynchronous requests for an Internet resource.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5a70-106">El uso de llamadas sincrónicas en métodos de devolución de llamada asincrónica puede afectar gravemente al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="a5a70-106">Using synchronous calls in asynchronous callback methods can result in severe performance penalties.</span></span> <span data-ttu-id="a5a70-107">Las solicitudes de Internet realizadas con **WebRequest** y sus descendientes deben usar <xref:System.IO.Stream.BeginRead%2A?displayProperty=nameWithType> para leer la secuencia devuelta por el método <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a5a70-107">Internet requests made with **WebRequest** and its descendants must use <xref:System.IO.Stream.BeginRead%2A?displayProperty=nameWithType> to read the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a5a70-108">En el código de ejemplo siguiente se muestra cómo usar llamadas asincrónicas con la clase **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="a5a70-108">The following sample code demonstrates how to use asynchronous calls with the **WebRequest** class.</span></span> <span data-ttu-id="a5a70-109">El ejemplo es un programa de consola que toma un URI de la línea de comandos, solicita el recurso en el URI y, después, imprime datos en la consola cuando se reciben desde Internet.</span><span class="sxs-lookup"><span data-stu-id="a5a70-109">The sample is a console program that takes a URI from the command line, requests the resource at the URI, and then prints data to the console as it is received from the Internet.</span></span>  
  
 <span data-ttu-id="a5a70-110">El programa define dos clases para su propio uso: la clase **RequestState**, que pasa datos a través de llamadas asincrónicas, y la clase **ClientGetAsync**, que implementa la solicitud asincrónica en un recurso de Internet.</span><span class="sxs-lookup"><span data-stu-id="a5a70-110">The program defines two classes for its own use, the **RequestState** class, which passes data across asynchronous calls, and the **ClientGetAsync** class, which implements the asynchronous request to an Internet resource.</span></span>  
  
 <span data-ttu-id="a5a70-111">La clase **RequestState** conserva el estado de la solicitud en las llamadas a los métodos asincrónicos que dan servicio a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="a5a70-111">The **RequestState** class preserves the state of the request across calls to the asynchronous methods that service the request.</span></span> <span data-ttu-id="a5a70-112">Contiene la clase **WebRequest** e instancias <xref:System.IO.Stream> que incluyen la solicitud actual al recurso y la secuencia recibida en respuesta, un búfer que contiene los datos recibidos actualmente del recurso de Internet y un elemento <xref:System.Text.StringBuilder> con la respuesta completa.</span><span class="sxs-lookup"><span data-stu-id="a5a70-112">It contains **WebRequest** and <xref:System.IO.Stream> instances that contain the current request to the resource and the stream received in response, a buffer that contains the data currently received from the Internet resource, and a <xref:System.Text.StringBuilder> that contains the complete response.</span></span> <span data-ttu-id="a5a70-113">Se pasa una clase **RequestState** como parámetro de *estado* cuando el método <xref:System.AsyncCallback> está registrado con **WebRequest.BeginGetResponse**.</span><span class="sxs-lookup"><span data-stu-id="a5a70-113">A **RequestState** is passed as the *state* parameter when the <xref:System.AsyncCallback> method is registered with **WebRequest.BeginGetResponse**.</span></span>  
  
 <span data-ttu-id="a5a70-114">La clase **ClientGetAsync** implementa una solicitud asincrónica a un recurso de Internet y escribe la respuesta resultante en la consola.</span><span class="sxs-lookup"><span data-stu-id="a5a70-114">The **ClientGetAsync** class implements an asynchronous request to an Internet resource and writes the resulting response to the console.</span></span> <span data-ttu-id="a5a70-115">Contiene los métodos y las propiedades que se describen en la lista siguiente.</span><span class="sxs-lookup"><span data-stu-id="a5a70-115">It contains the methods and properties described in the following list.</span></span>  
  
- <span data-ttu-id="a5a70-116">La propiedad `allDone` contiene una instancia de la clase <xref:System.Threading.ManualResetEvent> que indica la finalización de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="a5a70-116">The `allDone` property contains an instance of the <xref:System.Threading.ManualResetEvent> class that signals the completion of the request.</span></span>  
  
- <span data-ttu-id="a5a70-117">El método `Main()` lee la línea de comandos y comienza la solicitud para el recurso de Internet especificado.</span><span class="sxs-lookup"><span data-stu-id="a5a70-117">The `Main()` method reads the command line and begins the request for the specified Internet resource.</span></span> <span data-ttu-id="a5a70-118">Crea la clase **WebRequest**`wreq` y **RequestState** `rs`, llama a **BeginGetResponse** para empezar a procesar la solicitud y, después, llama al método `allDone.WaitOne()` para que la aplicación no se cierre hasta que la devolución de llamada se complete.</span><span class="sxs-lookup"><span data-stu-id="a5a70-118">It creates the **WebRequest** `wreq` and the **RequestState** `rs`, calls **BeginGetResponse** to begin processing the request, and then calls the `allDone.WaitOne()`method so that the application will not exit until the callback is complete.</span></span> <span data-ttu-id="a5a70-119">Una vez que se ha leído la respuesta del recurso de Internet, `Main()` lo escribe en la consola y la aplicación finaliza.</span><span class="sxs-lookup"><span data-stu-id="a5a70-119">After the response is read from the Internet resource, `Main()` writes it to the console and the application ends.</span></span>  
  
- <span data-ttu-id="a5a70-120">El método `showusage()` escribe una línea de comandos de ejemplo en la consola.</span><span class="sxs-lookup"><span data-stu-id="a5a70-120">The `showusage()` method writes an example command line on the console.</span></span> <span data-ttu-id="a5a70-121">Lo llama `Main()` cuando no se proporciona ningún URI en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="a5a70-121">It is called by `Main()` when no URI is provided on the command line.</span></span>  
  
- <span data-ttu-id="a5a70-122">El método `RespCallBack()` implementa el método de devolución de llamada asincrónica para la solicitud de Internet.</span><span class="sxs-lookup"><span data-stu-id="a5a70-122">The `RespCallBack()` method implements the asynchronous callback method for the Internet request.</span></span> <span data-ttu-id="a5a70-123">Crea la instancia **WebResponse** que contiene la respuesta del recurso de Internet, obtiene la secuencia de respuesta y, después, comienza a leer de manera asincrónica los datos de la secuencia.</span><span class="sxs-lookup"><span data-stu-id="a5a70-123">It creates the **WebResponse** instance containing the response from the Internet resource, gets the response stream, and then starts reading the data from the stream asynchronously.</span></span>  
  
- <span data-ttu-id="a5a70-124">El método `ReadCallBack()` implementa el método de devolución de llamada asincrónica para leer la secuencia de respuesta.</span><span class="sxs-lookup"><span data-stu-id="a5a70-124">The `ReadCallBack()` method implements the asynchronous callback method for reading the response stream.</span></span> <span data-ttu-id="a5a70-125">Transfiere los datos recibidos del recurso de Internet a la propiedad **ResponseData** de la instancia **RequestState** y, después, comienza otra lectura asincrónica de la secuencia de respuesta hasta que no se devuelvan más datos.</span><span class="sxs-lookup"><span data-stu-id="a5a70-125">It transfers data received from the Internet resource into the **ResponseData** property of the **RequestState** instance, then starts another asynchronous read of the response stream until no more data is returned.</span></span> <span data-ttu-id="a5a70-126">Una vez que se han leído todos los datos, `ReadCallBack()` cierra la secuencia de respuesta y llama al método `allDone.Set()` para indicar que la respuesta completa está presente en **ResponseData**.</span><span class="sxs-lookup"><span data-stu-id="a5a70-126">Once all the data has been read, `ReadCallBack()` closes the response stream and calls the `allDone.Set()` method to indicate that the entire response is present in **ResponseData**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a5a70-127">Es fundamental que todas las secuencias de red estén cerradas.</span><span class="sxs-lookup"><span data-stu-id="a5a70-127">It is critical that all network streams are closed.</span></span> <span data-ttu-id="a5a70-128">Si no cierra todas las secuencias de solicitud y respuesta, la aplicación se quedará sin conexiones con el servidor y no podrá procesar más solicitudes.</span><span class="sxs-lookup"><span data-stu-id="a5a70-128">If you do not close each request and response stream, your application will run out of connections to the server and be unable to process additional requests.</span></span>  
  
```csharp  
using System;  
using System.Net;  
using System.Threading;  
using System.Text;  
using System.IO;  
  
// The RequestState class passes data across async calls.  
public class RequestState  
{  
   const int BufferSize = 1024;  
   public StringBuilder RequestData;  
   public byte[] BufferRead;  
   public WebRequest Request;  
   public Stream ResponseStream;  
   // Create Decoder for appropriate enconding type.  
   public Decoder StreamDecode = Encoding.UTF8.GetDecoder();  
  
   public RequestState()  
   {  
      BufferRead = new byte[BufferSize];  
      RequestData = new StringBuilder(String.Empty);  
      Request = null;  
      ResponseStream = null;  
   }
}  
  
// ClientGetAsync issues the async request.  
class ClientGetAsync
{  
   public static ManualResetEvent allDone = new ManualResetEvent(false);  
   const int BUFFER_SIZE = 1024;  
  
   public static void Main(string[] args)
   {  
      if (args.Length < 1)
      {  
         showusage();  
         return;  
      }  
  
      // Get the URI from the command line.  
      Uri httpSite = new Uri(args[0]);  
  
      // Create the request object.  
      WebRequest wreq = WebRequest.Create(httpSite);  
  
      // Create the state object.  
      RequestState rs = new RequestState();  
  
      // Put the request into the state object so it can be passed around.  
      rs.Request = wreq;  
  
      // Issue the async request.  
      IAsyncResult r = (IAsyncResult) wreq.BeginGetResponse(  
         new AsyncCallback(RespCallback), rs);  
  
      // Wait until the ManualResetEvent is set so that the application
      // does not exit until after the callback is called.  
      allDone.WaitOne();  
  
      Console.WriteLine(rs.RequestData.ToString());  
   }  
  
   public static void showusage() {  
      Console.WriteLine("Attempts to GET a URL");  
      Console.WriteLine("\r\nUsage:");  
      Console.WriteLine("   ClientGetAsync URL");  
      Console.WriteLine("   Example:");  
      Console.WriteLine("      ClientGetAsync http://www.contoso.com/");  
   }  
  
   private static void RespCallback(IAsyncResult ar)  
   {  
      // Get the RequestState object from the async result.  
      RequestState rs = (RequestState) ar.AsyncState;  
  
      // Get the WebRequest from RequestState.  
      WebRequest req = rs.Request;  
  
      // Call EndGetResponse, which produces the WebResponse object  
      //  that came from the request issued above.  
      WebResponse resp = req.EndGetResponse(ar);
  
      //  Start reading data from the response stream.  
      Stream ResponseStream = resp.GetResponseStream();  
  
      // Store the response stream in RequestState to read
      // the stream asynchronously.  
      rs.ResponseStream = ResponseStream;  
  
      //  Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead  
      IAsyncResult iarRead = ResponseStream.BeginRead(rs.BufferRead, 0,
         BUFFER_SIZE, new AsyncCallback(ReadCallBack), rs);
   }  
  
   private static void ReadCallBack(IAsyncResult asyncResult)  
   {  
      // Get the RequestState object from AsyncResult.  
      RequestState rs = (RequestState)asyncResult.AsyncState;  
  
      // Retrieve the ResponseStream that was set in RespCallback.
      Stream responseStream = rs.ResponseStream;  
  
      // Read rs.BufferRead to verify that it contains data.
      int read = responseStream.EndRead( asyncResult );  
      if (read > 0)  
      {  
         // Prepare a Char array buffer for converting to Unicode.  
         Char[] charBuffer = new Char[BUFFER_SIZE];  
  
         // Convert byte stream to Char array and then to String.  
         // len contains the number of characters converted to Unicode.  
      int len =
         rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0);  
  
         String str = new String(charBuffer, 0, len);  
  
         // Append the recently read data to the RequestData stringbuilder  
         // object contained in RequestState.  
         rs.RequestData.Append(  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read));
  
         // Continue reading data until
         // responseStream.EndRead returns –1.  
         IAsyncResult ar = responseStream.BeginRead(
            rs.BufferRead, 0, BUFFER_SIZE,
            new AsyncCallback(ReadCallBack), rs);  
      }  
      else  
      {  
         if(rs.RequestData.Length>0)  
         {  
            //  Display data to the console.  
            string strContent;
            strContent = rs.RequestData.ToString();  
         }  
         // Close down the response stream.  
         responseStream.Close();
         // Set the ManualResetEvent so the main thread can exit.  
         allDone.Set();
      }  
      return;  
   }
}  
```  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Threading  
Imports System.Text  
Imports System.IO  
  
' The RequestState class passes data across async calls.  
Public Class RequestState  
  
      Public RequestData As New StringBuilder("")  
      Public BufferRead(1024) As Byte  
      Public Request As HttpWebRequest  
      Public ResponseStream As Stream  
      ' Create Decoder for appropriate encoding type.  
      Public StreamDecode As Decoder = Encoding.UTF8.GetDecoder()  
  
      Public Sub New  
         Request = Nothing  
         ResponseStream = Nothing  
      End Sub  
End Class  
  
' ClientGetAsync issues the async request.  
Class ClientGetAsync  
   Shared allDone As New ManualResetEvent(False)  
      Const BUFFER_SIZE As Integer = 1024  
  
    Shared Sub Main()  
        Dim Args As String() = Environment.GetCommandLineArgs()  
  
        If Args.Length < 2 Then  
            ShowUsage()  
            Return  
        End If  
  
      ' Get the URI from the command line.  
        Dim HttpSite As Uri = New Uri(Args(1))  
  
      ' Create the request object.  
        Dim wreq As HttpWebRequest = _  
           CType(WebRequest.Create(HttpSite), HttpWebRequest)  
  
      ' Create the state object.  
      Dim rs As RequestState = New RequestState()  
  
      ' Put the request into the state so it can be passed around.  
      rs.Request = wreq  
  
      ' Issue the async request.  
        Dim r As IAsyncResult = _  
           CType(wreq.BeginGetResponse( _  
           New AsyncCallback(AddressOf RespCallback), rs), IAsyncResult)  
  
      ' Wait until the ManualResetEvent is set so that the application  
      ' does not exit until after the callback is called.  
        allDone.WaitOne()  
    End Sub  
  
    Shared Sub ShowUsage()  
        Console.WriteLine("Attempts to GET a URI")  
        Console.WriteLine()  
        Console.WriteLine("Usage:")  
        Console.WriteLine("ClientGetAsync URI")  
        Console.WriteLine("Examples:")  
        Console.WriteLine("ClientGetAsync http://www.contoso.com/")  
    End Sub  
  
    Shared Sub RespCallback(ar As IAsyncResult)  
       ' Get the RequestState object from the async result.  
       Dim rs As RequestState = CType(ar.AsyncState, RequestState)  
  
       ' Get the HttpWebRequest from RequestState.  
       Dim req As HttpWebRequest= rs.Request  
  
       ' Call EndGetResponse, which returns the HttpWebResponse object  
       ' that came from the request issued above.  
       Dim resp As HttpWebResponse = _  
           CType(req.EndGetResponse(ar), HttpWebResponse)  
  
       ' Start reading data from the response stream.  
       Dim ResponseStream As Stream = resp.GetResponseStream()  
  
       ' Store the reponse stream in RequestState to read  
       ' the stream asynchronously.  
       rs.ResponseStream = ResponseStream  
  
       ' Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead.  
       Dim iarRead As IAsyncResult = _  
          ResponseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
          New AsyncCallback(AddressOf ReadCallBack), rs)  
    End Sub  
  
   Shared Sub ReadCallBack(asyncResult As IAsyncResult)  
      ' Get the RequestState object from the AsyncResult.  
      Dim rs As RequestState = CType(asyncResult.AsyncState, RequestState)  
  
      ' Retrieve the ResponseStream that was set in RespCallback.  
      Dim responseStream As Stream = rs.ResponseStream  
  
      ' Read rs.BufferRead to verify that it contains data.  
      Dim read As Integer = responseStream.EndRead( asyncResult )  
      If read > 0 Then  
         ' Prepare a Char array buffer for converting to Unicode.  
         Dim charBuffer(1024) As Char  
  
         ' Convert byte stream to Char array and then String.  
         ' len contains the number of characters converted to Unicode.  
         Dim len As Integer = _  
           rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0)  
         Dim str As String = new String(charBuffer, 0, len)
  
         ' Append the recently read data to the RequestData stringbuilder
         ' object contained in RequestState.  
         rs.RequestData.Append( _  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read))  
  
         ' Continue reading data until responseStream.EndRead  
         ' returns –1.  
         Dim ar As IAsyncResult = _  
            responseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
            New AsyncCallback(AddressOf ReadCallBack), rs)  
      Else  
          If rs.RequestData.Length > 1 Then  
            ' Display data to the console.  
            Dim strContent As String  
            strContent = rs.RequestData.ToString()  
            Console.WriteLine(strContent)  
         End If  
  
         ' Close down the response stream.  
         responseStream.Close()  
  
         ' Set the ManualResetEvent so the main thread can exit.  
         allDone.Set()  
      End If  
  
      Return  
   End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5a70-129">Vea también</span><span class="sxs-lookup"><span data-stu-id="a5a70-129">See also</span></span>

- [<span data-ttu-id="a5a70-130">Solicitud de datos</span><span class="sxs-lookup"><span data-stu-id="a5a70-130">Requesting Data</span></span>](requesting-data.md)
