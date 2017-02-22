---
title: "Verwaltetes Debuggen: Empfohlene Eigenschafteneinstellungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Verwaltet"
  - "Debuggen von verwaltetem Code, Empfohlene Eigenschafteneinstellungen"
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Verwaltetes Debuggen: Empfohlene Eigenschafteneinstellungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bestimmte Eigenschaften sollten für alle Szenarios des verwalteten Debuggens gleich festgelegt werden.  
  
 Die folgenden Tabellen zeigen die empfohlenen Eigenschafteneinstellungen.  
  
 Die hier nicht aufgeführten Einstellungen können je nach verwaltetem Projekttyp unterschiedlich sein.  So wird beispielweise die Einstellung für **Startaktion** in einem Windows Forms\-Projekt anders als in einem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Projekt festgelegt.  
  
### Konfigurationseigenschaften auf der Registerkarte Erstellen \(C\#\) oder auf der Registerkarte Kompilieren \(Visual Basic\)  
  
|**Eigenschaftenname**|**Einstellung**|  
|---------------------------|---------------------|  
|**DEBUG\-Konstante definieren**|C\# und F\#: Kontrollkästchen aktivieren.  Dadurch kann die Anwendung die Debug\-Klasse verwenden.|  
|**TRACE\-Konstante definieren**|C\# und F\#: Kontrollkästchen aktivieren.  Dadurch kann die Anwendung die Trace\-Klasse verwenden.|  
|**Code optimieren**|C\#, F\# und Visual Basic: Auf false festlegen.  Optimierter Code ist schwieriger zu debuggen, da die generierten Anweisungen nicht direkt mit dem Quellcode übereinstimmen.  Wenn das Programm einen Fehler aufweist, der nur im optimierten Code auftritt, können Sie diese Einstellung aktivieren. Beachten Sie jedoch, dass der im **Disassemblyfenster** angezeigte Code aus optimiertem Code generiert wurde, der u. U. nicht mit dem Code im Code\-Editor übereinstimmt.  Um optimierten Code zu debuggen, müssen Sie Nur mein Code deaktivieren. \(Weitere Informationen finden Sie unter [Schrittweises Durchlaufen für "Nur mein Code" beschränken](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).\)<br /><br /> Weitere Informationen finden Sie unter [Projekteinstellungen für C\#\-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md) oder [Projekteinstellungen für eine Visual Basic\-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Ausgabepfad**|Legen Sie als Ausgabepfad "bin\\Debug\\" fest.|  
|**Erweiterte Kompilierungsoptionen**|nur Visual Basic.  Klicken Sie auf **Erweitert**, um die erweiterten Eigenschaften festzulegen, die in der folgenden Tabelle beschrieben werden.|  
  
### Dialogfeld "Erweiterte Compilereinstellungen"  
  
|**Eigenschaftenname**|**Einstellung**|  
|---------------------------|---------------------|  
|**Optimierungen aktivieren**|Legen Sie die Einstellung auf false fest. Die Gründe hierfür finden Sie in der vorherigen Tabelle unter der Option **Code optimieren**.|  
|**Debuginformationen generieren**|Aktivieren Sie das Kontrollkästchen, damit das \/DEBUG\-Flag beim Kompilieren festgelegt wird. Dadurch werden Informationen generiert, die das Debuggen erleichtern.|  
|**DEBUG\-Konstante definieren**|Aktivieren Sie dieses Kontrollkästchen, um die `DEBUG`\-Konstante zu definieren. Dadurch kann die Anwendung die <xref:System.Diagnostics.Debug>\-Klasse verwenden.|  
|**TRACE\-Konstante definieren**|Aktivieren Sie dieses Kontrollkästchen, um die `TRACE`\-Konstante zu definieren. Dadurch kann die Anwendung die <xref:System.Diagnostics.Trace>\-Klasse verwenden.|  
  
## Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [C\#\-, F\#\- und Visual Basic\-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)