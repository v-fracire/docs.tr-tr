---
title: HttpWebRequest._CoreResponse Field
ms.date: 01/29/2018
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.author: stwhi
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: e6493747cf6c894357223f011da026770778e26c
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="httpwebrequestcoreresponse-field"></a><span data-ttu-id="63000-102">HttpWebRequest. \_CoreResponse alan</span><span class="sxs-lookup"><span data-stu-id="63000-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="63000-103">`HttpWebRequest._CoreResponse`bir nesne (ya da bir [CoreResponseData](coreresponsedata.md) veya bir <xref:System.Exception>) HTTP yanıt ayrıştırma sonucunu içeren.</span><span class="sxs-lookup"><span data-stu-id="63000-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="63000-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63000-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="63000-105">Bu API, kodunuzda doğrudan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="63000-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="63000-106">Bunun yerine, kullanmanız bir <xref:System.Diagnostics.DiagnosticSource> ağ kod bağlanmanıza.</span><span class="sxs-lookup"><span data-stu-id="63000-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="63000-107">Bkz: [DiagnosticSource Kullanıcı Kılavuzu](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="63000-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="63000-108">Microsoft hiçbir koşulda bir üretim uygulamasında bu sınıf kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="63000-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="63000-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63000-109">Requirements</span></span>

<span data-ttu-id="63000-110">**Namespace:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="63000-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="63000-111">**Derleme:** sisteminde (System.dll)</span><span class="sxs-lookup"><span data-stu-id="63000-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="63000-112">**.NET framework sürümleri:** 2.0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63000-112">**.NET Framework versions:** Available since 2.0.</span></span>