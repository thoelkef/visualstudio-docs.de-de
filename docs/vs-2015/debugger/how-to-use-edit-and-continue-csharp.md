---
title: 'Vorgehensweise: Bearbeiten und Fortfahren verwenden (C#) | Microsoft-Dokumentation'
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
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c52540c8e639adcd8ceec6b4da79fb87cff18386
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958091"
---
# <a name="how-to-use-edit-and-continue-c"></a>Vorgehensweise: Verwenden von „Bearbeiten und Fortfahren“ [C#]
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit Bearbeiten und Fortfahren für C# können Sie beim Debuggen Codeänderungen im Unterbrechungsmodus vornehmen. Die Änderungen können übernommen werden, ohne die Debugsitzung anhalten und neu starten zu müssen.  
  
 Bearbeiten und Fortfahren wird automatisch aufgerufen, wenn Änderungen im Unterbrechungsmodus befindet, und wählen Sie dann einen Ausführungsbefehl des Debuggers Befehl, z. B. **Weiter**, **Schritt**, oder **Festlegen der nächsten Anweisung**, oder für die Auswertung einer Funktion in einem Debuggerfenster.  
  
> [!NOTE]
>  Die Funktion "Bearbeiten und Fortfahren" wird beim Debuggen von Compact Framework, optimiertem Code, gemischtem systemeigenem/verwaltetem Code und SQL Server Common Language Runtime (CLR)-Integrationscode nicht unterstützt. Bei dem Versuch, in einem solchen Szenario Codeänderungen vorzunehmen, wird im Debugger ein Dialogfeld mit dem Hinweis angezeigt, dass Bearbeiten und Fortfahren nicht unterstützt wird.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>So rufen Sie Bearbeiten und Fortfahren automatisch auf  
  
1.  Nehmen Sie im Unterbrechungsmodus eine Änderung am Quellcode vor.  
  
2.  Von der **Debuggen** Menü klicken Sie auf **Weiter**, **Schritt**, oder **Festlegen der nächsten Anweisung** oder Auswerten einer Funktion in einem Debuggerfenster.  
  
     Der neue Code wird kompiliert, und das Debuggen wird mit neuem Code fortgesetzt. Einige Änderungen werden von Bearbeiten und Fortfahren nicht unterstützt. Weitere Informationen finden Sie unter [Supported Code Changes (C#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>So aktivieren bzw. deaktivieren Sie "Bearbeiten und Fortfahren"  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** Dialogfeld erweitern Sie die **Debuggen** Knoten, und wählen **bearbeiten und Fortfahren**.  
  
3.  In der **Optionen** Dialogfeld **bearbeiten und Fortfahren** Seite aktivieren oder Deaktivieren der **bearbeiten und Fortfahren aktivieren** Kontrollkästchen.  
  
     Die Einstellungen werden beim Neustarten der Debugsitzung aktiv.  
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten und Fortfahren (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Unterstützte Codeänderungen (C#)](../debugger/supported-code-changes-csharp.md)   
 [Bearbeiten und Fortfahren: Fehlermeldungen und Warnungen (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)
