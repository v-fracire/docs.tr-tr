---
title: ExportNestedType Metodu
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0afe4daa1c85f3e15addac55bdbe631d40e03f19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407576"
---
# <a name="exportnestedtype-method"></a>ExportNestedType Metodu
İç içe geçmiş türler verilebilir olarak belirtir. [ExportType yöntemi](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) iç içe geçmiş verme türlerini de kullanabilirsiniz, ancak bu daha hızlı bir yöntemdir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
#### <a name="parameters"></a>Parametreler  
 `AssemblyID`  
 Dışarı aktarmak için derleme kimliği.  
  
 `FileToken`  
 Dosya belirteci veya derleme dosyasının dışa aktarılabilir duruma getirilmek üzere türü tanımlar.  
  
 `TypeToken`  
 Dışarı aktarılabilir yapılması türünde belirteç yazın.  
  
 `ParentType`  
 Üst tür belirteci.  
  
 `pszTypename`  
 Dışarı aktarmak için tam olarak nitelenmiş tür adı.  
  
 `dwFlags`  
 `ComType` gibi bayrakları `tdPublic` veya `tdNested`. Bu değer için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Dışarı aktarılan tür için belirteci alır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 ALink.h gerektirir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IALink Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 Arabirimi](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
