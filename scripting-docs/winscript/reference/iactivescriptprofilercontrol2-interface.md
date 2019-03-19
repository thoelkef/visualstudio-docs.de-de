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
ms.openlocfilehash: 11987054ed934f4004333f136ea35696ff6c394f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147006"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>IActiveScriptProfilerControl2-Schnittstelle
Enthält Methoden, die addieren die Möglichkeit zum Starten oder Beenden der profilerstellung, wenn ein Skript ausgeführt wird.  
  
## <a name="methods"></a>Methoden  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Benachrichtigt den Profiler an, Sie begonnen haben, die profilerstellung auf allen anwendbaren Skript-Engines. Dadurch können Sie die vollständige Aufrufliste zu erhalten, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] wird ausgeführt, wenn Sie mit der profilerstellung beginnen.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Benachrichtigt den Profiler an, dass Sie beabsichtigen, die profilerstellung für alle anwendbaren Skript-Engines zu beenden. Dadurch können Sie die vollständige Aufrufliste zu erhalten, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ausgeführt wird, wenn Sie die profilerstellung beenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerControl-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [Active Script-Profilerschnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)