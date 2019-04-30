---
title: Debugger-eigenschafteneinstellungen für empfohlene C#, VB | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 711a8c1e8353f6e57f7101549a3b5421a33e0ae4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846285"
---
# <a name="managed-debugging-recommended-property-settings"></a>Verwaltetes Debuggen: Empfohlene Eigenschafteneinstellungen
Bestimmte Eigenschaften sollten für alle Szenarios des verwalteten Debuggens gleich festgelegt werden.

 Die folgenden Tabellen zeigen die empfohlenen Eigenschafteneinstellungen.

 Die hier nicht aufgeführten Einstellungen können je nach verwaltetem Projekttyp unterschiedlich sein. So wird beispielweise die Einstellung für **Startaktion[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in einem Windows Forms-Projekt anders als in einem** -Projekt festgelegt.

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Konfigurationseigenschaften auf der Registerkarte Erstellen (C#) oder auf der Registerkarte Kompilieren (Visual Basic)

|**Eigenschaftenname**|**Einstellung**|
|-----------------------|-----------------|
|**DEBUG-Konstante definieren**|C#und F#: Legen Sie das Kontrollkästchen aktiviert. Dadurch kann die Anwendung die Debug-Klasse verwenden.|
|**TRACE-Konstante definieren**|C#und F#: Legen Sie das Kontrollkästchen aktiviert. Dadurch kann die Anwendung die Trace-Klasse verwenden.|
|**Code optimieren**|C#, F#, und Visual Basic: Legen Sie auf "false". Optimierter Code ist schwieriger zu debuggen, da die generierten Anweisungen nicht direkt mit dem Quellcode übereinstimmen. Wenn das Programm einen Fehler aufweist, der nur im optimierten Code auftritt, können Sie diese Einstellung aktivieren. Beachten Sie jedoch, dass der im Fenster **Disassembly** angezeigte Code aus optimiertem Code generiert wurde, der möglicherweise nicht mit dem Code im Code-Editor übereinstimmt. Um optimierten Code zu debuggen, müssen Sie Nur mein Code deaktivieren. (Weitere Informationen finden Sie unter [Restrict stepping to Just My Code (Schrittweises Durchlaufen auf „Nur eigenen Code“ beschränken)](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).)<br /><br /> Weitere Informationen finden Sie unter [Projekteinstellungen für c# Debug Configurations](../debugger/project-settings-for-csharp-debug-configurations.md) oder [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|
|**Ausgabepfad**|Legen Sie als Ausgabepfad „bin\Debug\\\“ fest.|
|**Erweiterte Kompilierungsoptionen**|nur Visual Basic. Klicken Sie auf **Erweitert**, um die erweiterten Eigenschaften festzulegen, die in der folgenden Tabelle beschrieben werden.|

### <a name="advanced-compiler-settings-dialog-box"></a>Dialogfeld "Erweiterte Compilereinstellungen"

|**Eigenschaftenname**|**Einstellung**|
|-----------------------|-----------------|
|**Optimierungen aktivieren**|Legen Sie auf "false" für die Gründe hierfür der **Codeoptimierung** -Option in der obigen Tabelle.|
|**Debuginformationen generieren**|Aktivieren Sie das Kontrollkästchen, damit das /DEBUG-Flag beim Kompilieren festgelegt wird. Dadurch werden Informationen generiert, die das Debuggen erleichtern.|
|**DEBUG-Konstante definieren**|Aktivieren Sie dieses Kontrollkästchen, um die `DEBUG`-Konstante zu definieren. Dadurch kann die Anwendung die <xref:System.Diagnostics.Debug>-Klasse verwenden.|
|**TRACE-Konstante definieren**|Aktivieren Sie dieses Kontrollkästchen, um die `TRACE`-Konstante zu definieren. Dadurch kann die Anwendung die <xref:System.Diagnostics.Trace>-Klasse verwenden.|

## <a name="see-also"></a>Siehe auch
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)