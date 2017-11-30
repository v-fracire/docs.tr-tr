---
title: "&lt;giriş&gt; &lt;ekleme&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d62236c604cd91c2dfe4b92cfaac4004fc18d439
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltentriesgt"></a>&lt;giriş&gt; &lt;ekleme&gt;
Önceden tanımlanmış bir istemci uç noktası bir filtre eşlemeleri bir yönlendirme girişi temsil eder. Bu filtre ile eşleşen iletileri bu hedefe gönderilir.  
  
 \<system.serviceModel >  
\<Yönlendirme >  
\<routingTables >  
\<Tablo >  
\<girişleri >  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|backupList|Yedekleme bitiş noktaları listesini bir başvuru belirten bir dize.|  
|uç noktası|Tarafından belirtilen filtreyle eşleşen iletileri alacak olan bir istemci uç noktası için bir başvuru belirten bir dize `filterName` özniteliği.|  
|filterName|Bir filtre öğesi başvuru belirten bir dize.|  
|önceliği|Bu girdi önceliğini belirten bir tamsayı.<br /><br /> Yönlendirme tablosundaki girdileri öncelik sırasına göre en düşük önceliği olan 0 ile göre değerlendirilir. Tüm girişleri için belirli bir öncelik eşzamanlı olarak değerlendirilir, eşleşme olmaması durumunda giriş bulundu geçerli önceliği, sonraki öncelik düzeyi değerlendirilir.<br /><br /> Bu değer isteğe bağlıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Yönlendirme eşleme girdileri içeren bir yapılandırma bölümü.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 