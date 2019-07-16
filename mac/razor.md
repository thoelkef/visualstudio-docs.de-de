---
title: Razor
description: Informationen zur Razor-Unterstützung in ASP.NET Core-Apps in Visual Studio für Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: F898CB6E-05ED-44CD-8DB6-427B2592CCC6
ms.openlocfilehash: 9e5a3f61ee7065a0615a381bdcc03dafc3566893
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691269"
---
# <a name="razor"></a>Razor

Visual Studio für Mac bietet Unterstützung für die Bearbeitung mit Razor, einschließlich IntelliSense und Syntaxhervorhebung in *CSHTML*-Dateien.

![Bearbeitung mit Razor in Visual Studio für Mac](media/razor-editor.png)

Dieser Leitfaden bietet eine Einführung in die Erstellung Ihrer ersten Razor-Web-App. Detailliertere Anleitungen finden Sie in der [.NET Core-Dokumentation zu Razor Pages](/aspnet/core/razor-pages/index).

## <a name="creating-a-new-razor-project"></a>Erstellen eines neuen Razor-Projekts

* Wählen Sie auf der Willkommensseite **Neu** aus, um ein neues Projekt zu erstellen:

![Neues Projekt in Visual Studio für Mac](media/razor-new.png)

* Navigieren Sie im Dialogfeld „Neues Projekt“ zu **.NET Core** > **App** > **Webanwendung**, und klicken Sie auf die Schaltfläche **Weiter**:

![Razor-Projektvorlage](media/razor-new-project1.png)

* Wählen Sie das erforderliche .NET Core-Zielframework aus (2.2 oder höher wird empfohlen), und klicken Sie auf **Weiter**.  Wählen Sie einen Namen für Ihr Projekt aus, und fügen Sie bei Bedarf Git-Unterstützung hinzu. Wählen Sie **Create** (Erstellen), um das Projekt zu erstellen.

![Razor-Projektname](media/razor-new-project2.png)

Visual Studio für Mac öffnet Ihr Projekt im Codelayout.

* Führen Sie das Projekt mit **BEFEHLSTASTE+WAHLTASTE+F5** ohne Debuggen aus.

Visual Studio startet [Kestral](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), öffnet einen Browser auf der Seite `https://localhost:5001` und zeigt Ihre erste Razor-Web-App an:

![Razor-Web-App in Safari](media/razor-webapp.png)

## <a name="project-anatomy"></a>Projektanatomie

Razor-Web-Apps bestehen aus folgenden Komponenten:

### <a name="pages-folder"></a>Ordner „Seiten“

Der Ordner „Seiten“ im Projekt enthält die Webseiten sowie das CodeBehind für jede Seite:
* Eine * *.cshtml*-Datei für das HTML-Markup und die Razor-Syntax.
* Eine * *.cshtml.cs*-Datei für das C#-CodeBehind zum Verarbeiten von Seitenereignissen.

Unterstützende Dateien haben Namen, die mit einem Unterstrich beginnen. Die Datei „_Layout.cshtml“ beispielsweise konfiguriert Benutzeroberflächenelemente, die für alle Seiten gelten. Mit dieser Datei werden das Navigationsmenü oben auf der Seite und der Urheberrechtshinweis unten auf der Seite eingerichtet. Weitere Informationen finden Sie unter [Layout in ASP.NET Core](https://docs.microsoft.com/aspnet/core/mvc/views/layout).

### <a name="launch-settings"></a>Starteinstellungen

Die Datei *launchSettings.json* enthält die IIS-Einstellungen, Anwendungs-URL und weitere zugehörige Einstellungen.

### <a name="app-settings"></a>App-Einstellungen

Die Datei *appSettings.json* enthält Konfigurationsdaten wie z.B. Verbindungszeichenfolgen.

Weitere Informationen zur Konfiguration finden Sie unter [Konfiguration in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/index).

### <a name="wwwroot-folder"></a>Ordner „wwwroot“

Enthält statische Dateien, z. B. HTML-Dateien, JavaScript-Dateien und CSS-Dateien. Weitere Informationen finden Sie unter [Statische Dateien in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/static-files).

### <a name="programcs"></a>Program.cs

Enthält den Einstiegspunkt für das Programm. Weitere Informationen finden Sie unter [ASP.NET Core-Webhost](https://docs.microsoft.com/aspnet/core/fundamentals/host/web-host).

### <a name="startupcs"></a>Startup.cs

Enthält Code, mit dem das App-Verhalten konfiguriert wird, beispielsweise, ob die App Zustimmung für Cookies erfordert. Weitere Informationen finden Sie unter [Anwendungsstart in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/startup).

## <a name="see-aso"></a>Siehe auch:

Eine umfassendere Anleitung zum Erstellen von Razor-Web-Apps finden Sie unter [Einführung in Razor Pages in ASP.NET Core](https://docs.microsoft.com/aspnet/core/razor-pages/index).
