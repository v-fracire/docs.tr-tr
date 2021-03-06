---
title: Icordebugthread Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 404f1bdf5865733648084e34a558b7b20a59b3ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423084"
---
# <a name="icordebugthread-interface1"></a>Icordebugthread Interface1
Bir işlemdeki bir iş parçacığını temsil eder. Yaşam süresi bir `ICorDebugThread` örneğidir temsil ettiği iş parçacığı ömrü ile aynı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Bu yöntem uygulanmadı. Onu kullanmayın.|  
|[CreateEval Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Bu bilgisayarda çalışır Icordebugeval nesneyi oluşturur `ICorDebugThread`.|  
|[CreateStepper Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Bu etkin çerçevede doğruluk izin veren bir ICorDebugStepper nesnesi oluşturur `ICorDebugThread`.|  
|[EnumerateChains Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Arabirim işaretçisi bu tüm yığın zincirleri içeren bir Icordebugchainenum Numaralandırıcı alır `ICorDebugThread`.|  
|[GetActiveChain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Bu bilgisayarda etkin Icordebugchain arabirimi işaretçisi alır `ICorDebugThread`.|  
|[GetActiveFrame Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Bu bilgisayarda etkin Icordebugframe arabirimi işaretçisi alır `ICorDebugThread`.|  
|[GetAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Bu uygulama etki alanı için bir arabirim işaretçisi alır `ICorDebugThread` gerçekleştirmektedir.|  
|[GetCurrentException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Icordebugvalue nesneye şu anda yönetilen kod tarafından oluşturulan bir özel durum temsil eden bir arabirim işaretçisi alır.|  
|[GetDebugState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Bu geçerli hata ayıklama durumu açıklayan bir CorDebugThreadState değeri alır `ICorDebugThread`.|  
|[GetHandle Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Geçerli işleme etkin bir parçası bu alır `ICorDebugThread`.|  
|[GetID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Bu etkin parçası geçerli işletim sistemi tanımlayıcısını alır `ICorDebugThread`.|  
|[GetObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Arabirim işaretçisi ortak dil çalışma zamanı (CLR) iş parçacığına alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Bu işlemin bir arabirim işaretçisi alır `ICorDebugThread` bir bölümünü oluşturur.|  
|[GetRegisterSet Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Bu ile ilişkilendirilen kayıt kümesi için bir arabirim işaretçisi alır `ICorDebugThread`.|  
|[GetUserState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Bu geçerli durumunu açıklayan CorDebugUserState değerlerin Bitsel bir birleşimi alır `ICorDebugThread`.|  
|[SetDebugState Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Bit düzeyinde bileşimini ayarlar `CorDebugThreadState` bu hata ayıklama durumunu açıklayan değerleri `ICorDebugThread`.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
