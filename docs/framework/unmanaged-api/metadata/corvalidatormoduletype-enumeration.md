---
title: CorValidatorModuleType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97e9ae5a7c35b4f9b6e2b4ca7e754b5b7480dfa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444146"
---
# <a name="corvalidatormoduletype-enumeration"></a>CorValidatorModuleType Numaralandırması
Bir modül türünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|Geçersiz bir tür modülüdür.|  
|`ValidatorModuleTypeMin`|En küçük değerini `CorValidatorModuleType` enum.|  
|`ValidatorModuleTypePE`|Modül bir taşınabilir yürütülebilir (PE) dosyasıdır.|  
|`ValidatorModuleTypeObj`|Modül bir .obj dosyasıdır.|  
|`ValidatorModuleTypeEnc`|Düzenle ve devam et hata ayıklayıcı oturum modülüdür.|  
|`ValidatorModuleTypeIncr`|Modül artımlı olarak yerleşik biridir.|  
|`ValidatorModuleTypeMax`|En büyük değerini `CorValidatorModuleType` enum.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
