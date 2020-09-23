---
title: Verwenden von „Bearbeiten und Fortfahren“ (C#) | Microsoft-Dokumentation
ms.date: 10/04/2018
ms.topic: how-to
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 18d11f552d486fd9ebd7a95323e327324de14108
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851852"
---
# <a name="how-to-use-edit-and-continue-c"></a>Vorgehensweise: Verwenden von „Bearbeiten und Fortfahren“ [C#]
Mit „Bearbeiten und Fortfahren“ können Sie beim Debuggen Änderungen an Ihrem Code im Unterbrechungsmodus vornehmen und diese auf den Code anwenden, ohne die Debugsitzung beenden und neu starten zu müssen.

„Bearbeiten und Fortfahren“ für C# erfolgt automatisch, wenn Sie im Unterbrechungsmodus Änderungen am Code vornehmen und anschließend das Debuggen fortsetzen, indem Sie **Weiter**, **Schritt** oder **Nächste Anweisung festlegen** verwenden, oder wenn Sie im Debuggerfenster eine Funktion auswerten.

Weitere Informationen hierzu finden Sie unter [Bearbeiten und Fortfahren (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>„Bearbeiten und Fortfahren“ wird für optimierten, gemischten Code oder für SQL Server Common Language Runtime (CLR)-Integrationscode nicht unterstützt. Informationen zu weiteren nicht unterstützten Szenarien finden Sie unter [Unterstützte Codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md). Wenn Sie in einem dieser Szenarien „Bearbeiten und Fortfahren“ versuchen, wird ein Meldungsfeld mit dem Hinweis angezeigt, dass „Bearbeiten und Fortfahren“ nicht unterstützt wird.

**So aktivieren oder deaktivieren Sie „Bearbeiten und Fortfahren“**

1. Wenn Sie sich in einer Debugsitzung befinden, beenden Sie das Debuggen (**Debuggen** > **Debuggen beenden** oder **UMSCHALT**+**F5**).

1. Aktivieren oder deaktivieren Sie in **Tools** > **Optionen** (oder **Debuggen** > **Optionen**) > **Debuggen** > **Allgemein** das Kontrollkästchen **„Bearbeiten und Fortfahren“ aktivieren**.

Die Einstellungen werden beim Starten oder Neustarten der Debugsitzung aktiv.

**So verwenden Sie „Bearbeiten und Fortfahren“**

1. Nehmen Sie während des Debuggens im Unterbrechungsmodus eine Änderung an Ihrem Quellcode vor.

1. Klicken Sie im Menü **Debuggen** auf **Weiter**, **Schritt** oder **Nächste Anweisung festlegen**, oder werten Sie eine Funktion in einem Debuggerfenster aus.

   Das Debuggen wird mit dem neuen, kompilierten Code fortgesetzt.

Einige Arten von Codeänderungen werden von „Bearbeiten und Fortfahren“ nicht unterstützt. Weitere Informationen finden Sie unter [Unterstützte Codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md).
