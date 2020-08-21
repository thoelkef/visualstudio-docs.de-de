---
title: Erstellen von Razor-Web-Apps
description: In diesem Artikel finden Sie Informationen zur Razor-Unterstützung in ASP.NET Core-Apps in Visual Studio für Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.topic: how-to
ms.openlocfilehash: 26575367d7aff2b92c64dc5d07068b4900b24e7f
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249541"
---
# <a name="create-razor-web-apps"></a>Erstellen von Razor-Web-Apps

Dieser Leitfaden bietet eine Einführung in die Erstellung Ihrer ersten Razor-Web-App. Weitere ausführliche Anweisungen finden Sie unter [Einführung in Razor Pages in ASP.NET Core](/aspnet/core/razor-pages/index).

Visual Studio für Mac bietet Unterstützung für die Bearbeitung mit Razor, einschließlich IntelliSense und Syntaxhervorhebung in *CSHTML*-Dateien. Ab Visual Studio 2019 für Mac 8.3 ist kontextbezogenes IntelliSense in Razor-Dateien möglich, damit Sie IntelliSense-Daten empfangen, die mit der Sprache übereinstimmen, in der Sie aktuell in einem Dokument arbeiten.

![Bearbeitung mit Razor in Visual Studio für Mac](media/razor-2019.png)

## <a name="creating-a-new-razor-project"></a>Erstellen eines neuen Razor-Projekts

1. Klicken Sie auf der Willkommensseite auf **Neu**, um ein neues Projekt zu erstellen:

   ![Neues Projekt in Visual Studio für Mac](media/razor-new.png)
1. Navigieren Sie im Dialogfeld **Neues Projekt** zu **.NET Core** > **App** > **Webanwendung**, und klicken Sie dann auf **Weiter**:

   ![Razor-Projektvorlage](media/razor-new-project1.png)
1. Wählen Sie Ihr .NET Core-Zielframework aus (Version 2.2 oder höher wird empfohlen), und klicken Sie dann auf **Weiter**. Wählen Sie einen Namen für Ihr Projekt aus, und fügen Sie bei Bedarf Git-Unterstützung hinzu. Wählen Sie **Erstellen** aus, um das Projekt zu erstellen.

   ![Razor-Projektname](media/razor-new-project2.png)

   Visual Studio für Mac öffnet Ihr Projekt im Codelayoutfenster.
1. Führen Sie das Projekt mit **BEFEHLSTASTE+WAHLTASTE+F5** ohne Debuggen aus.

   Visual Studio startet [Kestrel](/aspnet/core/fundamentals/servers/kestrel), öffnet `https://localhost:5001` in einem Browser und zeigt Ihre erste Razor-Web-App an.

   ![Razor-Web-App in Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Projektanatomie

Razor-Web-Apps enthalten die folgenden Komponenten.

### <a name="pages-folder"></a>Ordner „Seiten“

Dieser Ordner enthält die Webseiten eines Projekts sowie das jeweilige CodeBehind für die Seiten:
- Eine *\*.cshtml*-Datei für das HTML-Markup und die Razor-Syntax.
- Eine *\*.cshtml.cs*-Datei für das C#-CodeBehind zum Verarbeiten von Seitenereignissen.

Unterstützende Dateien haben Namen, die mit einem Unterstrich beginnen. Die Datei *\_Layout.cshtml* konfiguriert beispielsweise Benutzeroberflächenelemente, die für alle Seiten gelten. Mit dieser Datei werden das Navigationsmenü oben und der Urheberrechtshinweis unten auf der Seite eingerichtet. Weitere Informationen finden Sie unter [Layout in ASP.NET Core](/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Starteinstellungen

Die Datei *launchSettings.json* enthält die IIS-Einstellungen, die Anwendungs-URL und weitere zugehörige Einstellungen.

### <a name="app-settings"></a>App-Einstellungen

Die Datei *appSettings.json* enthält Konfigurationsdaten wie Verbindungszeichenfolgen.

Weitere Informationen zur Konfiguration finden Sie unter [Konfiguration in ASP.NET Core](/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Ordner „wwwroot“

Dieser Ordner enthält statische Dateien, z. B. HTML-, JavaScript- und CSS-Dateien. Weitere Informationen finden Sie unter [Statische Dateien in ASP.NET Core](/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Diese Datei enthält den Einstiegspunkt für das Programm. Weitere Informationen finden Sie unter [ASP.NET Core-Webhost](/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Diese Datei enthält Code, mit dem das App-Verhalten konfiguriert wird, z. B., ob die App Zustimmung für Cookies erfordert. Weitere Informationen finden Sie unter [Anwendungsstart in ASP.NET Core](/aspnet/core/fundamentals/startup).

## <a name="see-also"></a>Siehe auch

Eine umfassendere Anleitung zum Erstellen von Razor-Web-Apps finden Sie unter [Einführung in Razor Pages in ASP.NET Core](/aspnet/core/razor-pages/index).
