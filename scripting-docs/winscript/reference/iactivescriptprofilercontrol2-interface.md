---
title: IActiveScriptProfilerControl2-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7059868ae65c5093b24f342bd303ec70172171c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571535"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2-Schnittstelle
Stellt Methoden bereit, die die Fähigkeit zum Starten oder Beenden der Profilerstellung beim Ausführen eines Skripts hinzufügen.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Benachrichtigt den Profiler, dass Sie die Profilerstellung für alle anwendbaren Skript-Engines gestartet haben. Auf diese Weise können Sie die gesamte-aufrufsstapel abrufen, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] beim Starten der Profilerstellung ausgeführt wird.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Benachrichtigt den Profiler, dass die Profilerstellung für alle anwendbaren Skript-Engines beendet werden soll. Dies ermöglicht es Ihnen, die komplette aufrufsstapel abzurufen, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ausgeführt wird, wenn Sie die Profilerstellung beenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Iactivescriptprofilercontrol-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol-interface.md)    
 [Active Script-Profilerschnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)