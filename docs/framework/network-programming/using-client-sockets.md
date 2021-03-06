---
title: İstemci yuvaları kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ee10681c8beddac06d5c4eae453f4070b2bf1b4e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195556"
---
# <a name="using-client-sockets"></a>İstemci yuvaları kullanma
Bir konuşma aracılığıyla başlatabilmesi bir <xref:System.Net.Sockets.Socket>, uygulamanızı hem de uzak cihazı veri kanalı oluşturmanız gerekir. Diğer ağ adresi ailelerini ve protokolleri mevcut olmasına karşın, bu örnek bir uzak hizmete bir TCP/IP bağlantısı oluşturma işlemi gösterilmektedir.  
  
 TCP/IP'yi hizmet benzersiz olarak tanımlanabilmesi için bir ağ adresi ve bir hizmet bağlantı noktası numarası kullanır. Ağ adresi, ağdaki belirli bir aygıt tanımlar; bağlantı noktası numarası, hizmete bağlanmak için bu cihazda tanımlar. Ağ adresi ve hizmet bağlantı noktası birleşimi .NET Framework tarafından temsil edilen bir uç nokta adı verilen <xref:System.Net.EndPoint> sınıfı. Bir alt öğesi **uç nokta** için tanımlanan her desteklenen Adres ailesi; IP adresi ailesi için sınıf <xref:System.Net.IPEndPoint>.  
  
 <xref:System.Net.Dns> Sınıfı TCP/IP'yi Internet Hizmetleri kullanan uygulamalar için etki alanı adı hizmetleri sağlar. <xref:System.Net.Dns.Resolve%2A> Yöntemi (Örneğin 192.168.1.1) sayısal bir Internet adresi için bir kullanıcı dostu bir etki alanı adı (örneğin, "host.contoso.com") eşlemek için bir DNS sunucusunu sorgular. **Çözmek** döndürür bir <xref:System.Net.IPHostEntry> , adresleri ve istenen ad için diğer adlar listesini içerir. Çoğu durumda, döndürülen ilk adresi kullanabileceğinizi <xref:System.Net.IPHostEntry.AddressList%2A> dizisi. Aşağıdaki kod alır bir <xref:System.Net.IPAddress> sunucu host.contoso.com IP adresini içeren.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Bağlantı noktası numaralarını (daha fazla bilgi için bkz: www.iana.org/assignments/port-numbers) ortak Hizmetleri için Internet Atanmış Numaralar Yetkilisi (IANA) tanımlar. Diğer hizmetler için 1024 65,535 aralığında bağlantı noktası numaralarını kayıtlı. Aşağıdaki kod host.contoso.com için IP adresi için bir bağlantı uzak uç noktası oluşturmak için bir bağlantı noktası numarası ile birleştirir.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Uzak cihaz adresi belirleme ve bağlantısı için kullanmak üzere bir bağlantı noktası seçme sonra uzak cihazla bağlantı kurmak uygulama deneyebilirsiniz. Aşağıdaki örnekte mevcut bir **IPEndPoint** uzak bir aygıta bağlanmayı ve oluşturulan özel durumları yakalar.  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman Uyumlu İstemci Yuvası Kullanma](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [Zaman Uyumsuz İstemci Yuvası Kullanma](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Nasıl Yapılır: Yuva Oluşturma](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [Yuvalar](../../../docs/framework/network-programming/sockets.md)
