---
title: 'Vorgehensweise: Verwenden von bearbeiten und Fortfahren (c#) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 10/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 41e97f488344e3d34ce326a3d35880d94da4ad9a
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382804"
---
# <a name="how-to-use-edit-and-continue-c"></a>Gewusst wie: Verwenden von "Bearbeiten und Fortfahren" (C#)
Sie können mit bearbeiten und Fortfahren stellen und Anwenden von Änderungen auf Ihren Code im Unterbrechungsmodus befindet, während des Debuggings, beenden und neu starten der Debugsitzung ohne.  

Bearbeitung und-Fortsetzung für C# erfolgt automatisch, wenn Sie codeänderungen im Unterbrechungsmodus vornehmen und dann fortfahren, Debuggen, indem Sie mithilfe von **Weiter**, **Schritt**, oder **Festlegen der nächsten Anweisung**, oder für die Auswertung einer Funktion in einem Debuggerfenster.  

Weitere Informationen finden Sie unter [bearbeiten und Fortfahren (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Bearbeiten und Fortfahren wird nicht unterstützt, für optimiert, mixed, oder SQL Server common Language Runtime (CLR)-Integrationscode. Weitere Informationen zu anderen nicht unterstützten Szenarien finden Sie unter [unterstützte codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md). Wenn Sie versuchen, bearbeiten und eines dieser Szenarien fortfahren, wird eine Meldung angezeigt, mit dem Hinweis, dass bearbeiten und Fortfahren wird nicht unterstützt.  
  
**So aktivieren oder deaktivieren, bearbeiten und Fortfahren:**  
   
1. Wenn Sie in einer Debugsitzung sind, beenden Sie das Debuggen (**Debuggen** > **Debuggen beenden** oder **UMSCHALT**+**F5**) .
   
1. In **Tools** > **Optionen** (oder **Debuggen** > **Optionen**) > **Debuggen**  >  **Allgemeine**aktivieren oder Deaktivieren der **bearbeiten und Fortfahren aktivieren** Kontrollkästchen.  
  
Die Einstellung wird wirksam, wenn beim Starten oder die Debugsitzung neu starten.  

**So verwenden Sie bearbeiten und Fortfahren:**  
   
1. Nehmen Sie während des Debuggens im Unterbrechungsmodus eine Änderung am Quellcode.  
   
1. Aus der **Debuggen** Menü klicken Sie auf **Weiter**, **Schritt**, oder **Festlegen der nächsten Anweisung**, oder für die Auswertung einer Funktion in einem Debuggerfenster.  
   
   Debuggen wird durch den neuen, kompilierte Code fortgesetzt. 

Einige Arten von codeänderungen werden durch Bearbeiten und Fortfahren nicht unterstützt. Weitere Informationen finden Sie unter [unterstützte codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md).   
