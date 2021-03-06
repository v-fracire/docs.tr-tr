---
title: ICorDebugRegisterSet::GetRegisters Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: deaeb4e244a4f9c1e8582d9bea26c2ae5cfde818
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421357"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters Metodu
Her kayıt değerini (kod şu anda yürütülmekte bilgisayarda) alır bit maskesi kullanılarak belirtilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `mask`  
 [in] Bir bit maskesi alınacak değerler hangi kaydı belirtir. Her bitin bir kasaya karşılık gelir. Bir bit birine ayarlanırsa, kasanın değer alınır; Aksi takdirde kasanın değeri alınamadı.  
  
 `regCount`  
 [in] Alınacak kayıt değerlerinin sayısı.  
  
 `regBuffer`  
 [out] Bir dizi `CORDB_REGISTER` nesneleri, her biri bir kayıt değeri alır.  
  
## <a name="remarks"></a>Açıklamalar  
 Dizinin boyutu bir bit maskesi için bitler sayısına eşit olmalıdır. `regCount` Parametresi kayıt değerlerini alacak arabellek öğe sayısını belirtir. Varsa `regCount` değeri maskesiyle belirtilen yazmaçlar sayısı için çok küçük, daha yüksek numaralı yazmaçlar kümesinden kesilir. Varsa `regCount` değer çok büyük, kullanılmayan `regBuffer` öğeleri değiştirilmemiş olacaktır.  
  
 Bit maskesi kullanılamıyor, bir kayıt belirtiyorsa `GetRegisters` konusu kasaya belirsiz bir değer döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugRegisterSet Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [ICorDebugRegisterSet2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
