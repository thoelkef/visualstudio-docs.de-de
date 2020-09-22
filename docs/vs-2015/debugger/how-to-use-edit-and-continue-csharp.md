---
title: 'Vorgehensweise: Verwenden von „Bearbeiten und Fortfahren“ (C#) | Microsoft-Dokumentation'
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
ms.openlocfilehash: 39137d5fe60a3c91c8fd3904e797eb83420a8f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841064"
---
# <a name="how-to-use-edit-and-continue-c"></a>Vorgehensweise: Verwenden von „Bearbeiten und Fortfahren“ [C#]
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit Bearbeiten und Fortfahren für C# können Sie beim Debuggen Codeänderungen im Unterbrechungsmodus vornehmen. Die Änderungen können übernommen werden, ohne die Debugsitzung anhalten und neu starten zu müssen.  
  
 "Bearbeiten und Fortfahren" wird automatisch aufgerufen, wenn Sie Änderungen im Break-Modus vornehmen. Wählen Sie dann einen Debugger-Ausführungs Befehl aus, z. b. **fortsetzen**, **Schritt**oder **nächste Anweisung festlegen**, oder Werten Sie eine Funktion in einem Debuggerfenster aus.  
  
> [!NOTE]
> Die Funktion "Bearbeiten und Fortfahren" wird beim Debuggen von Compact Framework, optimiertem Code, gemischtem systemeigenem/verwaltetem Code und SQL Server Common Language Runtime (CLR)-Integrationscode nicht unterstützt. Bei dem Versuch, in einem solchen Szenario Codeänderungen vorzunehmen, wird im Debugger ein Dialogfeld mit dem Hinweis angezeigt, dass Bearbeiten und Fortfahren nicht unterstützt wird.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>So rufen Sie Bearbeiten und Fortfahren automatisch auf  
  
1. Nehmen Sie im Unterbrechungsmodus eine Änderung am Quellcode vor.  
  
2. Klicken Sie im Menü **Debuggen** auf **weiter**, **Schritt**oder **nächste Anweisung festlegen** , oder Werten Sie eine Funktion in einem Debuggerfenster aus.  
  
     Der neue Code wird kompiliert, und das Debuggen wird mit neuem Code fortgesetzt. Einige Änderungen werden von Bearbeiten und Fortfahren nicht unterstützt. Weitere Informationen finden Sie [unter Unterstützte Code Änderungen (c#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>So aktivieren bzw. deaktivieren Sie "Bearbeiten und Fortfahren"  
  
1. Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2. Erweitern Sie im Dialogfeld **Optionen** den Knoten **Debuggen** , und wählen Sie **Bearbeiten und Fortfahren**aus.  
  
3. Aktivieren bzw. deaktivieren Sie im Dialogfeld **Optionen** auf der Seite **Bearbeiten und Fortfahren** das Kontrollkästchen **Bearbeiten und Fortfahren aktivieren** .  
  
     Die Einstellungen werden beim Neustarten der Debugsitzung aktiv.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bearbeiten und Fortfahren (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Unterstützte Code Änderungen (c#)](../debugger/supported-code-changes-csharp.md)   
 [Bearbeiten und Fortfahren mit Fehlern und Warnungen (c#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)
