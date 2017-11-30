---
title: "AssemblyBindInfo Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyBindInfo
helpviewer_keywords: AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f23c8269c7dd7f85ad0f848c1dee2ed0bf903c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo Yapısı
Başvurulan derlemeyi hakkında ayrıntılı bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`dwAppDomainId`|İçin benzersiz bir tanımlayıcı `IStream` yapılan bir çağrı tarafından döndürülen [Ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), başvurulan derlemeyi yüklenecek olan gelen.|  
|`lpReferencedIdentity`|Başvurulan derlemeyi için benzersiz bir tanımlayıcı.|  
|`lpPostPolicyIdentity`|Başvurulan derlemeyi sonra herhangi bir bağlama ilke değeri uygulama için tanımlayıcı.|  
|`ePolicyLevel`|Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hangi sürüm oluşturma ilkeleri varsa, başvurulan derlemeyi uygulanması gereken gösteren değerler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Benzersiz tanımlayıcı ana bilgisayar kaynakları `dwAppDomainId` ortak dil çalışma zamanı (CLR) için. Çağrı sonra `IHostAssemblyStore::ProvideAssembly` döndürür, çalışma zamanı belirlemek için tanımlayıcısını kullanır olup olmadığını içeriğini `IStream` eşlenmedi. Bu durumda, çalışma zamanı akış yeniden eşleme yerine var olan kopyasını yükler. Akışlar döndürülen için çalışma zamanı bu tanımlayıcı ayrıca arama anahtar olarak kullanır. çağrılar [Ihostassemblystore::providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md). Bu nedenle, tanımlayıcı derleme isteklerini ve modül isteği için benzersiz olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.idl  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma yapıları](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [Iclrassemblyıdentitymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Iclrassemblyreferencelist arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Ihostassemblymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [Ihostassemblystore arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [Modulebindınfo yapısı](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)