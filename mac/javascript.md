---
title: JavaScript und TypeScript
description: Informationen über die Unterstützung für JavaScript in Visual Studio für Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 13aa6e595deb83344d40dff396c7e106bdcbc67e
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108032"
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
- **JSDoc** – In manchen Situationen stellt der Typrückschluss nicht die richtigen Typinformationen bereit. In diesen Fällen können die Typinformationen explizit durch [JSDoc](https://jsdoc.app/about-getting-started.html)-Anmerkungen bereitgestellt werden. Weitere Informationen finden Sie im Abschnitt über Visual Studio unter [IntelliSense (auf JSDoc basierend)](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc).
- **TypeScript-Deklarationsdateien:** `.d.ts`-Dateien werden verwendet, um Werte für JavaScript-IntelliSense bereitzustellen. In dieser Datei deklarierte Typen können als Typen in JSDoc-Kommentaren verwendet werden. Weitere Informationen finden Sie im Abschnitt über Visual Studio unter [IntelliSense (auf TypeScript-Deklarationsdateien basierend)](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files)

    ![Hinzufügen einer TypeScript-Definitionsdatei](media/javascript-image3.png)

## <a name="see-also"></a>Siehe auch

- [JavaScript IntelliSense (Visual Studio unter Windows)](/visualstudio/ide/javascript-intellisense)
