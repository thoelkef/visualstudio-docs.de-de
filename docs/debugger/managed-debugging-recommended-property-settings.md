---
title: 'Verwaltetes Debuggen: Empfohlene Eigenschafteneinstellungen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e1c4b725871012f1fbf2c80f3e978f133d4db5b0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="managed-debugging-recommended-property-settings"></a>Verwaltetes Debuggen: Empfohlene Eigenschafteneinstellungen
Bestimmte Eigenschaften sollten für alle Szenarios des verwalteten Debuggens gleich festgelegt werden.  
  
 Die folgenden Tabellen zeigen die empfohlenen Eigenschafteneinstellungen.  
  
 Die hier nicht aufgeführten Einstellungen können je nach verwaltetem Projekttyp unterschiedlich sein. Z. B. **Startaktion** wird anders festgelegt werden, in einem Windows Forms-Projekt als in einem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Projekt.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Konfigurationseigenschaften auf der Registerkarte Erstellen (C#) oder auf der Registerkarte Kompilieren (Visual Basic)  
  
|**Eigenschaftenname**|**Einstellung**|  
|-----------------------|-----------------|  
|**DEBUG-Konstante definieren**|C# und F#: Kontrollkästchen aktivieren. Dadurch kann die Anwendung die Debug-Klasse verwenden.|  
|**TRACE-Konstante definieren**|C# und F#: Kontrollkästchen aktivieren. Dadurch kann die Anwendung die Trace-Klasse verwenden.|  
|**Code optimieren**|C#, F# und Visual Basic: Auf false festlegen. Optimierter Code ist schwieriger zu debuggen, da die generierten Anweisungen nicht direkt mit dem Quellcode übereinstimmen. Wenn Sie feststellen, das Programm einen Fehler aufweist, der nur im optimierten Code auftritt, können Sie diese Einstellung aktivieren, aber beachten Sie, Pseudocode der **Disassembly** aus optimiertem, die nicht entsprechen möglicherweise sehen Sie im Code generiert wurde -Editor. Um optimierten Code zu debuggen, müssen Sie Nur mein Code deaktivieren. (Siehe [schrittweises Durchlaufen für nur mein Code beschränken](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Weitere Informationen finden Sie unter [Projekteinstellungen für C#-Debug Configurations](../debugger/project-settings-for-csharp-debug-configurations.md) oder [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Ausgabepfad**|Legen Sie auf "bin\Debug"\\.|  
|**Erweiterte Kompilierungsoptionen**|nur Visual Basic. Klicken Sie auf **erweitert** die erweiterten Eigenschaften festzulegen, die beschrieben werden in der folgenden Tabelle.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>Dialogfeld "Erweiterte Compilereinstellungen"  
  
|**Eigenschaftenname**|**Einstellung**|  
|-----------------------|-----------------|  
|**Optimierungen aktivieren**|Auf "false" festgelegt werden, für die Gründe, die im angegebenen der **Codeoptimierung** -Option in der obigen Tabelle.|  
|**Debuginformationen generieren**|Aktivieren Sie das Kontrollkästchen, damit das /DEBUG-Flag beim Kompilieren festgelegt wird. Dadurch werden Informationen generiert, die das Debuggen erleichtern.|  
|**DEBUG-Konstante definieren**|Aktivieren Sie dieses Kontrollkästchen, um die `DEBUG`-Konstante zu definieren. Dadurch kann die Anwendung die <xref:System.Diagnostics.Debug>-Klasse verwenden.|  
|**TRACE-Konstante definieren**|Aktivieren Sie dieses Kontrollkästchen, um die `TRACE`-Konstante zu definieren. Dadurch kann die Anwendung die <xref:System.Diagnostics.Trace>-Klasse verwenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)