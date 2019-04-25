---
title: JavaScript und TypeScript
description: Informationen über die Unterstützung für JavaScript in Visual Studio für Mac
author: conceptdev
ms.author: crdun
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: ed84e5478ae7a15905a5555a318bd656c664710e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982897"
---
# <a name="javascript-and-typescript-support"></a>Unterstützung für JavaScript und TypeScript

Visual Studio für Mac bietet Unterstützung für JavaScript und TypeScript über Syntaxhervorhebung, Codeformatierung und IntelliSense.

![TypeScript-Editor-Unterstützung](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

Weitere Informationen zum Schreiben von JavaScript finden Sie in den Anleitungen [Schreiben von JavaScript-Code](/scripting/javascript/writing-javascript-code).

## <a name="adding-a-javascript-file"></a>Hinzufügen einer JavaScript-Datei

JavaScript-Dateien werden am häufigsten über das Dialogfeld **Neue Datei** zu ASP.NET Core-Projekten hinzugefügt. Klicken Sie zum Hinzufügen einer JavaScript-Datei mit der rechten Maustaste auf Ihr Projekt, und wechseln Sie zu **Hinzufügen > Neue Datei**:

![Hinzufügen neuer Dateien zum Projekt](media/javascript-image1.png)

Wählen Sie im Dialogfeld **Neue Datei** **Web > Empty JS file** (Leere JS-Datei) oder **Web > TypeScript-Datei** aus. Benennen Sie die Datei, und wählen Sie dann **Neu** aus:

![Erstellen einer neuen TypeScript-Datei aus der Vorlage](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio für Mac verwendet den [JavaScript Language Service](/visualstudio/ide/javascript-intellisense) für die Bereitstellung von IntelliSense. Auf diese Weise verfügen Sie beim Schreiben von Code über eine intelligente Codevervollständigung, Parameterinfos und Memberlisten.

JavaScript-IntelliSense in Visual Studio für Mac kann auf einem Typrückschluss, einem JSDoc oder einer TypeScript-Deklaration basieren.

- **Typrückschluss** – Der Typ eines Objekts wird anhand des umgebenden Codekontexts ermittelt. Weitere Informationen finden Sie im Abschnitt über Visual Studio unter [IntelliSense (auf Typrückschluss basierend)](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **JSDoc** – In manchen Situationen stellt der Typrückschluss nicht die richtigen Typinformationen bereit. In diesen Fällen können die Typinformationen explizit durch [JSDoc](http://usejsdoc.org/about-getting-started.html)-Anmerkungen bereitgestellt werden. Weitere Informationen finden Sie im Abschnitt über Visual Studio unter [IntelliSense (auf JSDoc basierend)](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc).
- **TypeScript-Deklarationsdateien:** `.d.ts`-Dateien werden verwendet, um Werte für JavaScript-IntelliSense bereitzustellen. In dieser Datei deklarierte Typen können als Typen in JSDoc-Kommentaren verwendet werden. Weitere Informationen finden Sie im Abschnitt über Visual Studio unter [IntelliSense (auf TypeScript-Deklarationsdateien basierend)](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files)

    ![Hinzufügen einer TypeScript-Definitionsdatei](media/javascript-image3.png)

## <a name="see-also"></a>Siehe auch

- [JavaScript IntelliSense (Visual Studio unter Windows)](/visualstudio/ide/javascript-intellisense)
