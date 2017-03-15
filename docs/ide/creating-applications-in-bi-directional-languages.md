---
title: Erstellen von Anwendungen in bidirektionalen Sprachen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 011e576a17b268fb3710c72de70d6260dc6117a4
ms.lasthandoff: 02/22/2017

---
# <a name="creating-applications-in-bi-directional-languages"></a>Erstellen von Anwendungen in bidirektionalen Sprachen
Mit Visual Studio können Sie Anwendungen erstellen, die Text mit der Schreibrichtung von rechts nach links, einschließlich Arabisch und Hebräisch, korrekt anzeigen. Für einige Funktionen können Sie ganz einfach Eigenschaften festlegen. In anderen Fällen müssen Features im Code implementiert werden.  
  
> [!NOTE]
>  Um bidirektionale Sprachen anzeigen und eingeben zu können, müssen Sie mit einer Windows-Version arbeiten, in der die entsprechende Sprache konfiguriert ist. Entweder sollten Sie also eine englischsprachige Windows-Version und das entsprechende Sprachpaket installiert haben, oder Sie verwenden die entsprechende lokalisierte Windows-Version.  
  
## <a name="types-of-application-that-support-bi-directional-languages"></a>Anwendungstypen, die bidirektionale Sprachen unterstützen  
  
1.  Windows-Anwendungen. Sie können vollständig bidirektionale Anwendungen erstellen, die dann bidirektionalen Text, Rechts-nach-Links-Lesefolge und Spiegeln (Umkehren des Layouts von Fenstern, Menüs, Dialogfeldern usw.) unterstützen. Diese Features (mit Ausnahme von Spiegeln) sind standardmäßig oder als Eigenschaftseinstellungen verfügbar. Spiegeln wird für einige Features wie Meldungsfelder grundsätzlich unterstützt. In anderen Fällen muss das Spiegeln jedoch im Code implementiert werden. Weitere Informationen finden Sie unter [Bidirektionale Unterstützung für Windows Forms-Anwendungen](http://msdn.microsoft.com/Library/7b622fa4-f390-4e4d-b624-83a1917cccf2).  
  
2.  Webanwendungen. Webdienste unterstützen das Senden und Empfangen von mit UTF-8 oder Unicode codiertem Text und sind daher für Anwendungen, die bidirektionalen Text verwenden, geeignet. Webclientanwendungen verwenden als Benutzeroberfläche den Browser. Wie gut Bidirektionalität bei Webanwendungen unterstützt wird, hängt also davon ab, wie gut der Browser des jeweiligen Benutzers diese bidirektionalen Funktionen unterstützt. Mit Visual Studio können Sie Anwendungen erstellen, die arabischen oder hebräischen Text, Rechts-nach-Links-Lesefolge, Dateicodierung und lokale Kultureinstellungen unterstützen. Weitere Informationen finden Sie unter [Bidirektionale Unterstützung für ASP.NET-Webanwendung](http://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).  
  
3.  Konsolenanwendungen Konsolenanwendungen unterstützen keinen bidirektionalen Text. Das liegt an der Art und Weise, wie Windows Konsolenanwendungen einsetzt.  
  
## <a name="visual-studio-features-that-are-fully-supported"></a>Visual Studio-Funktionen, die vollständig unterstützt werden  
 Zur Entwurfszeit sind bidirektionale Sprachen in Visual Studio folgendermaßen einsetzbar:  
  
-   **Texteingabe** Visual Studio unterstützt Unicode. Wenn in Ihrem System also das entsprechende Gebietsschema und die entsprechende Eingabesprache eingestellt sind, können Sie Text auf Arabisch oder Hebräisch eingeben. (Ebenso werden auch Kashida und Diakritika unterstützt.)  
  
-   **Objektnamen** Mithilfe von bidirektionalen Sprachen können Sie Projektmappen, Projekten, Dateien, Ordern usw. Namen zuweisen. Im Code können Sie bidirektionale Sprachen zum Benennen von Variablen, Klassen, Objekten, Attributen, Metadaten und anderen Elementen einsetzen.  
  
-   **Dateicodierung** Sie können Dateien mit sprachspezifischer oder Unicode-Codierung speichern und öffnen. Weitere Informationen finden Sie unter [Vorgehensweise: Speichern und Öffnen von Dateien mit Codierung](../ide/how-to-save-and-open-files-with-encoding.md).  
  
## <a name="features-with-limited-or-no-support"></a>Nicht oder nur eingeschränkt unterstützte Funktionen  
 Einige Features, die für Anwendungen in bidirektionalen Sprachen üblich sind, werden von Visual Studio nur eingeschränkt oder gar nicht unterstützt. Dazu gehören:  
  
-   **Rechts-nach-Links-Lesefolge** Die Steuerelemente für die Texteingabe von Visual Studio verwenden standardmäßig die Lesefolge von links nach rechts. Meist können Sie die Lesefolge mit Windows-Standardfunktionen ändern. So können Sie z. B. mit STRG+RECHTE UMSCHALTTASTE das Eigenschaftenfenster umschalten, sodass für die Eigenschaftswerte die Lesefolge von rechts nach links unterstützt wird.  
  
     Die Lesefolge von rechts nach links wird jedoch nicht überall in Visual Studio unterstützt. Zu den Ausnahmen zählen:  
  
    -   Kontrollkästchen, Dropdownlisten und andere Steuerelemente verwenden in Visual Studio immer die Lesefolge von links nach rechts.  
  
    -   Der Code-Editor (und der Text-Editor) unterstützen die Lesefolge von rechts nach links nicht. Sie können zwar Text in einer bidirektionalen Sprache eingeben, doch die Lesefolge bleibt stets von links nach rechts.  
  
## <a name="naming-things-using-arabic-or-hebrew-text"></a>Benennung mit arabischem oder hebräischem Text  
 Sie können mithilfe von arabischem oder hebräischem Text Ordnern, Variablen oder anderen Objekten Namen zuweisen. Wenn Sie mit Arabisch arbeiten, können Sie alle arabischen Zeichen verwenden, einschließlich Kashida und Diakritika.  
  
 Folgende Elemente können mithilfe von Arabisch oder Hebräisch benannt werden und werden in Visual Studio korrekt gehandhabt:  
  
-   Projektmappen-, Projekt- und Dateinamen, einschließlich aller dem Projektpfad hinzugefügten Ordner. Die Namen der Projektmappen und Elemente werden dann im Projektmappen-Explorer korrekt angezeigt.  
  
-   Dateiinhalt. Sie können mit Unicode codierte Dateien oder Dateien mit einer ausgewählten Codepage öffnen und speichern.  
  
    > [!NOTE]
    >  Der Code-Editor ist ein Sonderfall. Einzelheiten finden Sie weiter unten.  
  
-   Datenelemente. Diese Elemente werden im **Server-Explorer** korrekt angezeigt, und Sie können sie bearbeiten.  
  
-   In die Windows-Zwischenablage kopierte Elemente.  
  
-   Attribute und Metadaten.  
  
-   Eigenschaftswerte. Sie können im Fenster Eigenschaften arabischen oder hebräischen Text eingeben. In diesem Fenster können Sie mit den üblichen Windows-Tastenkombinationen zwischen der Rechts-nach-Links-Lesefolge und der Links-nach-Rechts-Lesefolge wechseln (STRG+RECHTE UMSCHALTTASTE für Rechts-nach-Links bzw. STRG+LINKE UMSCHALTTASTE für Links-nach-Rechts).  
  
-   Code und normaler Text. Im Code-Editor, der gleichzeitig der Text-Editor ist, können Sie mithilfe von Arabisch oder Hebräisch Klassen, Funktionen, Variablen, Eigenschaften, Zeichenfolgenliterale, Attribute usw. benennen. Allerdings unterstützt der Editor keine Lesefolge von rechts nach links; der Text beginnt immer am linken Rand.  
  
    > [!TIP]
    >  Es wird empfohlen, Zeichenfolgenliterale in Ressourcendateien abzulegen und sie nicht fest in Programmen zu codieren. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Lokalisieren von Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
    > [!NOTE]
    >  Die Verweise auf die in diesen Sprachen benannten Objekte müssen konsistent sein. Wenn Sie z. B. bei der Benennung einer arabischen Variablen Kashida verwenden, müssen Sie dies auch tun, wenn Sie auf diese Variable verweisen, sonst werden Fehler verursacht.  
  
-   Codekommentare. Sie können Kommentare in Arabisch oder Hebräisch erstellen. Sie können diese Sprachen auch im Kommentarerstellungstool verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Bidirektionale Unterstützung für Windows Forms-Anwendungen](http://msdn.microsoft.com/Library/7b622fa4-f390-4e4d-b624-83a1917cccf2)   
 [Bidirektionale Unterstützung für ASP.NET-Webanwendung](http://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03)   
 [Globalisieren von Anwendungen](../ide/globalizing-applications.md)   
 [Lokalisieren von Anwendungen](../ide/localizing-applications.md)
