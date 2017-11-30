---
title: IManagedObject::GetObjectIdentity Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IManagedObject.GetObjectIdentity
api_location: mscoree.dll
api_type: COM
f1_keywords: GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c0dabfca147b203c3bcf93a362e6670ae295338
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imanagedobjectgetobjectidentity-method"></a>IManagedObject::GetObjectIdentity Metodu
Bu yönetilen nesne kimliğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pBSTRGUID`  
 [out] Bir işaretçi nesne bulunduğu işlem GUID.  
  
 `AppDomainID`  
 [out] Nesnenin uygulama etki alanı kimliği için bir işaretçi.  
  
 `pCCW`  
 [out] COM Klasik v tablosunda nesnenin dizin için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilen bir nesnenin kimliğini işlemi GUID, uygulama etki alanı kimliği ve nesnenin dizin COM Klasik v tabloda içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IManagedObject arabirimi](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)