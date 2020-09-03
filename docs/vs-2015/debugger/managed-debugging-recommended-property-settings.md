---
title: 'Verwaltetes Debuggen: Empfohlene Eigenschaften Einstellungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f63e1382d242a679ed4fac09bfb3040200fed551
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203593"
---
# <a name="managed-debugging-recommended-property-settings"></a>Verwaltetes Debuggen: Empfohlene Eigenschafteneinstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bestimmte Eigenschaften sollten für alle Szenarios des verwalteten Debuggens gleich festgelegt werden.  
  
 Die folgenden Tabellen zeigen die empfohlenen Eigenschafteneinstellungen.  
  
 Die hier nicht aufgeführten Einstellungen können je nach verwaltetem Projekttyp unterschiedlich sein. So wird beispielweise die Einstellung für **Startaktion** in einem Windows Forms-Projekt anders als in einem [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Projekt festgelegt.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Konfigurationseigenschaften auf der Registerkarte Erstellen (C#) oder auf der Registerkarte Kompilieren (Visual Basic)  
  
|**Eigenschaftenname**|**Einstellung**|  
|-----------------------|-----------------|  
|**DEBUG-Konstante definieren**|C# and F#: Kontrollkästchen aktivieren. Dadurch kann die Anwendung die Debug-Klasse verwenden.|  
|**TRACE-Konstante definieren**|C# and F#: Kontrollkästchen aktivieren. Dadurch kann die Anwendung die Trace-Klasse verwenden.|  
|**Code optimieren**|C#, F# und Visual Basic: auf „false“ festlegen. Optimierter Code ist schwieriger zu debuggen, da die generierten Anweisungen nicht direkt mit dem Quellcode übereinstimmen. Wenn das Programm einen Fehler aufweist, der nur im optimierten Code auftritt, können Sie diese Einstellung aktivieren. Beachten Sie jedoch, dass der im Fenster **Disassembly** angezeigte Code aus optimiertem Code generiert wurde, der möglicherweise nicht mit dem Code im Code-Editor übereinstimmt. Zum Debuggen von optimiertem Code müssen Sie [nur eigenen Code](just-my-code.md)deaktivieren.<br /><br /> Weitere Informationen finden Sie unter [Projekteinstellungen für C#-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md) und [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Ausgabepfad**|Legen Sie als Ausgabepfad „bin\Debug\\\“ fest.|  
|**Erweiterte Kompilierungsoptionen**|nur Visual Basic. Klicken Sie auf **Erweitert**, um die erweiterten Eigenschaften festzulegen, die in der folgenden Tabelle beschrieben werden.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>Dialogfeld "Erweiterte Compilereinstellungen"  
  
|**Eigenschaftenname**|**Einstellung**|  
|-----------------------|-----------------|  
|**Optimierungen aktivieren**|Legen Sie die Einstellung auf „false“ fest. Die Gründe hierfür finden Sie in der vorherigen Tabelle unter der Option **Code optimieren**.|  
|**Debuginformationen generieren**|Aktivieren Sie das Kontrollkästchen, damit das /DEBUG-Flag beim Kompilieren festgelegt wird. Dadurch werden Informationen generiert, die das Debuggen erleichtern.|  
|**DEBUG-Konstante definieren**|Aktivieren Sie dieses Kontrollkästchen, um die `DEBUG`-Konstante zu definieren. Dadurch kann die Anwendung die <xref:System.Diagnostics.Debug>-Klasse verwenden.|  
|**TRACE-Konstante definieren**|Aktivieren Sie dieses Kontrollkästchen, um die `TRACE`-Konstante zu definieren. Dadurch kann die Anwendung die <xref:System.Diagnostics.Trace>-Klasse verwenden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugging von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
