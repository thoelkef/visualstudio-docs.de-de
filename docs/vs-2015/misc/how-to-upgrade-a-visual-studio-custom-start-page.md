---
title: 'Vorgehensweise: Aktualisieren einer benutzerdefinierten Startseite | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: 457b3baf2b291a0ef96bd8bbd748261348a2108d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045459"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Vorgehensweise: Aktualisieren einer benutzerdefinierten Startseite Visual Studio
Sie können eine benutzerdefinierte Visual Studio 2010- oder Visual Studio 2012-Startseite auf Visual Studio 2015 aktualisieren. Führen dazu die nachfolgenden Schritte aus.

> [!WARNING]
>  Bei der in dieser Vorgehensweise aktualisierten Startseite handelt es sich um die mit der Vorlage [Benutzerdefinierte Startseite](http://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) in der Visual Studio Gallery erstellte Startseite. Ihre Startseite weist möglicherweise andere Funktionen auf, die aktualisiert werden müssen.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>So aktualisieren Sie eine benutzerdefinierte Startseite auf Visual Studio 2015

1. Stellen Sie sicher, dass Visual Studio 2015 und Visual Studio 2015 SDK installiert sind. Sie können das VS SDK unter [Microsoft Visual Studio 2013 SDK](https://my.visualstudio.com/Downloads?pid=1436)herunterladen.

2. Öffnen Sie das benutzerdefinierte Vorlagenprojekt. Es wird die Meldung angezeigt, dass das Projekt aktualisiert wird. Klicken Sie auf **OK** , und warten Sie, bis die Aktualisierung beendet ist.

3. Vergewissern Sie sich, dass das Zielframework in den Projekteigenschaften für das Startseitenprojekt und das Verwaltungsprojekt mindestens .NET Framework 4.5 ist.

4. Legen Sie in der Debugkategorie der Projekteigenschaften für das Startseitenprojekt den Pfad auf die Visual Studio 2015-Version "devenv.exe" fest.

5. Entfernen Sie in den Projektverweisen für beide Projekte die Verweise auf Microsoft.VisualStudio.Shell.11.0, und fügen Sie Verweise auf Microsoft.VisualStudio.Shell.14.0 hinzu.

6. Öffnen Sie "StartPage.xaml" im XML-Editor, und nehmen Sie folgende Änderungen vor:

    1. Aktualisieren Sie die Namespaces. Ändern Sie die folgenden Zeilen:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         Folgendermaßen:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7. Öffnen Sie "MyControl.xaml", und ändern Sie den Namespaceverweis `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` in `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .