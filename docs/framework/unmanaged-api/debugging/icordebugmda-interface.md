---
title: ICorDebugMDA Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550b39445dfe4d97e712e9a4c73aa0f497b3fce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420972"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA Arabirimi
Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDescription Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|Bu MDA açıklamasını içeren bir dize alır.|  
|[GetFlags Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|Bu MDA ile ilişkili bayraklar alır.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|Bu MDA adını içeren bir dize alır.|  
|[GetOSThreadId Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|Bu MDA dosyanızın çalıştığı işletim sistemi iş parçacığı tanımlayıcısını alır.|  
|[GetXML Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|Bu MDA ile ilişkili tam XML akışı alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
