---
title: Unterstützung für Apps in den Sprachen Arabisch und Hebräisch
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display, creating applications
- bidirectional language support, about bidirectional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99df6eddcdd6f02e4cce8410762d3c0b9f00f29a
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450320"
---
# <a name="create-applications-in-bidirectional-languages"></a>Erstellen von Anwendungen in bidirektionalen Sprachen

Mit Visual Studio können Sie Anwendungen erstellen, die Text mit der Schreibrichtung von rechts nach links, einschließlich Arabisch und Hebräisch, korrekt anzeigen. Für einige Funktionen können Sie ganz einfach Eigenschaften festlegen. In anderen Fällen müssen Features im Code implementiert werden.

> [!NOTE]
> Wenn Sie bidirektionale Sprachen anzeigen und eingeben möchten, müssen Sie mit einer Windows-Version arbeiten, in der die entsprechende Sprache konfiguriert ist. Entweder sollten Sie also eine englischsprachige Windows-Version und das entsprechende Sprachpaket installiert haben, oder Sie verwenden die entsprechende lokalisierte Windows-Version.

## <a name="types-of-applications-that-support-bidirectional-languages"></a>Anwendungstypen, die bidirektionale Sprachen unterstützen

-  Windows-Apps

   Sie können vollständig bidirektionale Anwendungen erstellen, die dann bidirektionalen Text, die Rechts-nach-Links-Lesefolge und das Spiegeln (Umkehren des Layouts von Fenstern, Menüs, Dialogfeldern usw.) unterstützen. Diese Features (mit Ausnahme von Spiegeln) sind standardmäßig oder als Eigenschaftseinstellungen verfügbar. Spiegeln wird für einige Features wie Meldungsfelder grundsätzlich unterstützt. In anderen Fällen muss das Spiegeln jedoch im Code implementiert werden. Weitere Informationen finden Sie unter [bidirectional support for Windows Forms applications (Unterstützung von bidirektionalen Sprachen in Windows Forms-Anwendungen)](/dotnet/framework/winforms/advanced/bidirectional-support-for-windows-forms-applications).

-  Web-Apps

   Webdienste unterstützen das Senden und Empfangen von mit UTF-8 oder Unicode codiertem Text und sind daher für Anwendungen geeignet, die bidirektionale Sprachen verwenden. Webclientanwendungen verwenden als Benutzeroberfläche den Browser. Wie gut Bidirektionalität bei Webanwendungen unterstützt wird, hängt also davon ab, wie gut der Browser des jeweiligen Benutzers diese bidirektionalen Features unterstützt. Mit Visual Studio können Sie Anwendungen erstellen, die arabischen oder hebräischen Text, Rechts-nach-Links-Lesefolge, Dateicodierung und lokale Kultureinstellungen unterstützen. Weitere Informationen finden Sie unter [Bidirektionale Unterstützung für ASP.NET-Webanwendung](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

Konsolen-Apps unterstützen keinen Text für bidirektionale Sprachen. Das liegt an der Art und Weise, wie Windows Konsolenanwendungen einsetzt.

## <a name="fully-supported-features"></a>Vollständig unterstützte Funktionen

Zur Entwurfszeit sind bidirektionale Sprachen in Visual Studio folgendermaßen einsetzbar:

- **Texteingabe**

   Visual Studio unterstützt Unicode. Wenn in Ihrem System also das entsprechende Gebietsschema und die entsprechende Eingabesprache eingestellt sind, können Sie Text auf Arabisch oder Hebräisch eingeben. (Ebenso werden auch Kashida und Diakritika unterstützt.)

- **Objektnamen**

   Mithilfe von bidirektionalen Sprachen können Sie unter anderem Projektmappen, Projekten, Dateien und Ordern Namen zuweisen. Im Code können Sie bidirektionale Sprachen zum Benennen von Variablen, Klassen, Objekten, Attributen, Metadaten und anderen Elementen einsetzen.

- **Dateicodierung**

   Sie können Dateien mit sprachspezifischer oder Unicode-Codierung speichern und öffnen. Weitere Informationen finden Sie unter [Vorgehensweise: Speichern und Öffnen von Dateien mit Codierung](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="features-with-limited-support"></a>Features mit eingeschränkter Unterstützung

### <a name="right-to-left-reading-order"></a>Leserichtung von rechts nach links

Die Steuerelemente für die Texteingabe von Visual Studio verwenden standardmäßig die Leserichtung von links nach rechts. Meist können Sie die Lesefolge mit Windows-Standardfunktionen ändern. So können Sie z.B. mit **STRG**+**RECHTE UMSCHALTTASTE** das **Eigenschaftenfenster** umschalten, sodass für die Eigenschaftswerte die Leserichtung von rechts nach links unterstützt wird. Die Leserichtung von rechts nach links wird jedoch nicht überall in Visual Studio unterstützt.

- Kontrollkästchen, Dropdownlisten und andere Steuerelemente verwenden in Visual Studio immer die Lesefolge von links nach rechts.

- Der Code-Editor (und der Text-Editor) unterstützen die Lesefolge von rechts nach links nicht. Sie können zwar Text in einer bidirektionalen Sprache eingeben, doch die Lesefolge bleibt stets von links nach rechts.

## <a name="arabic-or-hebrew-object-names"></a>Arabische oder hebräische Objektnamen

Sie können mithilfe von arabischem oder hebräischem Text Ordnern, Variablen oder anderen Objekten Namen zuweisen. Wenn Sie mit Arabisch arbeiten, können Sie alle arabischen Zeichen verwenden, einschließlich Kashida und Diakritika.

Folgende Elemente können mithilfe von Arabisch oder Hebräisch benannt werden und werden in Visual Studio korrekt gehandhabt:

- Projektmappen-, Projekt- und Dateinamen, einschließlich aller dem Projektpfad hinzugefügten Ordner. Die Namen der Projektmappen und Elemente werden dann im **Projektmappen-Explorer** korrekt angezeigt.

- Dateiinhalt. Sie können mit Unicode codierte Dateien oder Dateien mit einer ausgewählten Codepage öffnen und speichern.

    > [!NOTE]
    > Der Code-Editor unterstützt die Leserichtung von rechts nach links nicht.

- Datenelemente. Diese Elemente werden im **Server-Explorer** korrekt angezeigt, und Sie können sie bearbeiten.

- In die Windows-Zwischenablage kopierte Elemente.

- Attribute und Metadaten.

- Eigenschaftswerte. Sie können im Fenster **Eigenschaften** arabischen oder hebräischen Text eingeben. In diesem Fenster können Sie mit den üblichen Windows-Tastenkombinationen zwischen der Leserichtung von rechts nach links und der Leserichtung von links nach rechts wechseln (**STRG**+**RECHTE UMSCHALTTASTE** für von rechts nach links bzw. **STRG**+**LINKE UMSCHALTTASTE** für von links nach rechts).

- Code und normaler Text. Im Code-Editor können Sie mithilfe von Arabisch oder Hebräisch Klassen, Funktionen, Variablen, Eigenschaften, Zeichenfolgenliterale, Attribute usw. benennen. Allerdings unterstützt der Editor keine Lesefolge von rechts nach links; der Text beginnt immer am linken Rand.

    > [!TIP]
    > Es wird empfohlen, Zeichenfolgenliterale in Ressourcendateien abzulegen und sie nicht fest in Programmen zu codieren. Weitere Informationen finden Sie unter [Ressourcen in Desktop-Apps](/dotnet/framework/resources/index).

    > [!NOTE]
    > Die Verweise auf die benannten Objekte in Arabisch und Hebräisch müssen konsistent sein. Wenn Sie z.B. bei der Benennung einer arabischen Variablen Kashida verwenden, müssen Sie dies auch tun, wenn Sie auf diese Variable verweisen, sonst werden Fehler verursacht.

- Codekommentare. Sie können Kommentare in Arabisch oder Hebräisch erstellen. Sie können diese Sprachen auch im Kommentarerstellungstool verwenden.