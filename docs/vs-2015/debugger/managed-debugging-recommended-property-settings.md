---
title: 'Verwaltetes Debuggen: Empfohlene Eigenschafteneinstellungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50fa9b61d017be3e860c10f11688bcd79f252969
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510561"
---
# <a name="managed-debugging-recommended-property-settings"></a>Verwaltetes Debuggen: Empfohlene Eigenschafteneinstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [verwaltete Debuggen: empfohlene Eigenschafteneinstellungen](https://docs.microsoft.com/visualstudio/debugger/managed-debugging-recommended-property-settings).  
  
Bestimmte Eigenschaften sollten für alle Szenarios des verwalteten Debuggens gleich festgelegt werden.  
  
 Die folgenden Tabellen zeigen die empfohlenen Eigenschafteneinstellungen.  
  
 Die hier nicht aufgeführten Einstellungen können je nach verwaltetem Projekttyp unterschiedlich sein. Z. B. **Startaktion** wird anders festgelegt werden, in einem Windows Forms-Projekt als in einem [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Projekt.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Konfigurationseigenschaften auf der Registerkarte Erstellen (C#) oder auf der Registerkarte Kompilieren (Visual Basic)  
  
|**Eigenschaftenname**|**Einstellung**|  
|-----------------------|-----------------|  
|**DEBUG-Konstante definieren**|C# und F#: Kontrollkästchen aktivieren. Dadurch kann die Anwendung die Debug-Klasse verwenden.|  
|**TRACE-Konstante definieren**|C# und F#: Kontrollkästchen aktivieren. Dadurch kann die Anwendung die Trace-Klasse verwenden.|  
|**Code optimieren**|C#, F# und Visual Basic: Auf false festlegen. Optimierter Code ist schwieriger zu debuggen, da die generierten Anweisungen nicht direkt mit dem Quellcode übereinstimmen. Wenn Sie feststellen, das Programm hat einen Fehler, der nur im optimierten Code auftritt, können Sie diese Einstellung aktivieren, aber denken Sie daran, im gezeigten Code der **Disassembly** aus optimiertem, die nicht mit Anzeige im Code generiert wurde Der Editor. Um optimierten Code zu debuggen, müssen Sie deaktivieren [nur mein Code](just-my-code.md).<br /><br /> Weitere Informationen finden Sie unter [Projekteinstellungen für c# Debug Configurations](../debugger/project-settings-for-csharp-debug-configurations.md) oder [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Ausgabepfad**|Legen Sie auf "bin\Debug"\\.|  
|**Erweiterte Kompilierungsoptionen**|nur Visual Basic. Klicken Sie auf **erweitert** auf die erweiterten Eigenschaften festzulegen, die beschrieben werden in der folgenden Tabelle.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>Dialogfeld "Erweiterte Compilereinstellungen"  
  
|**Eigenschaftenname**|**Einstellung**|  
|-----------------------|-----------------|  
|**Optimierungen aktivieren**|Legen Sie auf "false" für die Gründe hierfür der **Codeoptimierung** -Option in der obigen Tabelle.|  
|**Debuginformationen generieren**|Aktivieren Sie das Kontrollkästchen, damit das /DEBUG-Flag beim Kompilieren festgelegt wird. Dadurch werden Informationen generiert, die das Debuggen erleichtern.|  
|**DEBUG-Konstante definieren**|Aktivieren Sie dieses Kontrollkästchen, um die `DEBUG`-Konstante zu definieren. Dadurch kann die Anwendung die <xref:System.Diagnostics.Debug>-Klasse verwenden.|  
|**TRACE-Konstante definieren**|Aktivieren Sie dieses Kontrollkästchen, um die `TRACE`-Konstante zu definieren. Dadurch kann die Anwendung die <xref:System.Diagnostics.Trace>-Klasse verwenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)



