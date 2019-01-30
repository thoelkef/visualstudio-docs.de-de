---
title: VCMessage-Aufgabe| Microsoft-Dokumentation
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5543627332e7c70fa40df5be4091bca7fab7bcfd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004852"
---
# <a name="vcmessage-task"></a>VCMessage-Aufgabe
Protokolliert Warn- und Fehlermeldungen während eines Builds  
  
## <a name="remarks"></a>Hinweise  
 Diese Aufgabe unterstützt bei der Implementierung von MSBuild für Visual C++ und ist nicht dazu gedacht, vom Benutzer aufgerufen zu werden. Weitere Informationen finden Sie unter <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **VCMessage**-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|**Argumente**|Optionaler **String**-Parameter.<br /><br /> Eine durch Semikolons getrennte Liste der Nachrichten, die angezeigt werden sollen|  
|**Code**|Erforderlicher **String**-Parameter.<br /><br /> Eine Fehlernummer, die die Nachricht identifiziert|  
|**Type**|Optionaler **String**-Parameter.<br /><br /> Gibt die Art der auszugebenden Meldung an Gibt entweder „Warning“ an, um eine Warnung auszugeben, oder „Error“ für eine Fehlermeldung.|  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)