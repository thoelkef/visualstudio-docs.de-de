---
title: 'Vorgehensweise: Aktivieren und Deaktivieren von "Bearbeiten und Fortfahren" | Microsoft-Dokumentation'
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 2c8486bdcd7bc737d3851eabd88734df4efd80b7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430536"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Gewusst wie: Aktivieren und Deaktivieren von "Bearbeiten undC#fortfahren" C++(, VB,)

Sie können " **Bearbeiten und Fortfahren** " im Visual Studio-Dialogfeld " **Optionen** " zur Entwurfszeit deaktivieren oder aktivieren. Die Funktion **Bearbeiten und Fortfahren** funktioniert nur in Debugversionen. Weitere Informationen hierzu finden Sie unter [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

Für Native C++, **Bearbeiten und Fortfahren** erfordert die Verwendung der Option `/INCREMENTAL`. Weitere Informationen zu den Funktionsanforderungen in C++finden Sie in diesem [Blogbeitrag](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) und unter " [BearbeitenC++und Fortfahren" ()](../debugger/edit-and-continue-visual-cpp.md).

**So aktivieren oder deaktivieren Sie "Bearbeiten und Fortfahren":**

1. Wenn Sie sich in einer Debugsitzung befinden, können Sie das Debuggen**Abbrechen (Debuggen**  > **Debugging Abbrechen** oder **UMSCHALT** +**F5**)

1. Wählen Sie unter Extras  > **Optionen** > (oder **Debuggen**  > **Optionen**) > **Debugging**  > **Allgemein**aus, und klicken Sie im rechten **Bereich auf** **Bearbeiten und Fortfahren** .

    > [!NOTE]
    > Wenn IntelliTrace aktiviert ist und Sie IntelliTrace-Ereignisse und Aufrufinformationen erfassen, wird "Bearbeiten und Fortfahren" deaktiviert. Weitere Informationen finden Sie unter [IntelliTrace](../debugger/intellitrace.md).

1. Stellen C++ Sie für Code sicher, dass **native bearbeiten und Fortfahren aktivieren** ausgewählt ist, und legen Sie die zusätzlichen Optionen fest:
    - **Änderungen beim Fortfahren anwenden (nur nativ)**

      Wenn Sie diese Option auswählen, kompiliert Visual Studio automatisch Codeänderungen und wendet sie an, wenn Sie das Debuggen fortsetzen. Andernfalls können Sie Änderungen mithilfe von **Debug** - >  Anwenden von**Code Änderungen**auswählen.

    - **Warnung bei veraltetem Code (nur nativ)**

      Wenn diese Option ausgewählt ist, werden Warnungen zu veraltetem Code ausgegeben.

1. Klicken Sie auf **OK**.
