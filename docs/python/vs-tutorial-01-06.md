---
title: Arbeiten mit Python in Visual Studio, Schritt 6 | Microsoft-Dokumentation
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 8356a9d4ab470b67a6e495d753fa498237e530f4
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2017
---
# <a name="step-6-working-with-git"></a>Schritt 6: Arbeiten mit Git

**Vorheriger Schritt: [Installieren von Paketen und Verwalten Ihrer Python-Umgebung](vs-tutorial-01-05.md)**

Visual Studio bietet die direkte Integration mit lokalen Git-Repositorys und solchen, die sich in Diensten wie GitHub und Visual Studio Team Services befinden. Die Integration umfasst das Klonen eines Repositorys, das Übernehmen von Änderungen und das Verwalten von Branches.

In diesem Artikel wird das Erstellen eines lokalen Git-Repositorys für ein vorhandenes Projekt beschrieben. Eine exemplarische Vorgehensweise für das Erstellen eines Projekts über ein Git-Remoterepository finden Sie unter [Quickstart: clone a repository of Python code in Visual Studio (Schnellstart: Klonen eines Repositorys mit Python-Code in Visual Studio)](quickstart-03-project-from-repository.md).

1. Klicken Sie mit der rechten Maustaste auf die Projektmappe, und klicken Sie dann auf **Projektmappe zur Quellcodeverwaltung hinzufügen**, wenn ein Projekt (z.B. das Projekt aus dem [vorherigen Schritt](vs-tutorial-01-05.md)) in Visual Studio geöffnet ist. Visual Studio erstellt ein lokales Git-Repository, das Ihren Projektcode enthält und Git-bezogene Steuerelemente anzeigt, die ebenfalls am unteren Rand des Visual Studio-Fensters angezeigt werden. Die Steuerelemente zeigen ausstehende Commits, Änderungen, den Namen des Repositorys und den Branch an. Zeigen Sie auf die Steuerelemente, um zusätzliche Informationen anzuzeigen.

  ![Zusätzliche Informationen, die angezeigt werden, wenn auf ein Git-Steuerelement im Visual Studio-Fenster gezeigt wird](media/working-with-git-01.png)

1. Das **Team Explorer**-Fenster wird mit verschiedenen verfügbaren Git-Optionen angezeigt, indem Sie auf den Header des Repositorys klicken. Der im Folgenden dargestellte **Sync**-Bereich bietet Optionen für das Veröffentlichen auf einem Remoterepository.

  ![Team Explorer in Visual Studio, nachdem ein lokales Repository erstellt wurde](media/working-with-git-02.png)

1. Klicken Sie auf **Änderungen**, um nicht gespeicherte Änderungen zu überprüfen und diese bei Bedarf zu übernehmen.

  ![Team Explorer in Visual Studio, der nicht gespeicherte Änderungen anzeigt](media/working-with-git-03.png)

1. Klicken Sie auf **Branches**, um Branches zu untersuchen und Zusammenführungs- und Rebasevorgänge auszuführen.

  ![Team Explorer in Visual Studio, der Branches anzeigt](media/working-with-git-04.png)

1. Wenn Sie ein lokales Repository verwenden, werden gespeicherte Änderungen direkt an das Repository übertragen. Wenn Sie mit einem Remoterepository verbunden sind, klicken Sie auf **Sync**, um Ihre lokalen Commits mithilfe von Push zu übertragen.

## <a name="going-deeper"></a>Vertiefung

Ein ausführlicheres Tutorial für das Arbeiten mit Git finden Sie unter [Share your code with Visual Studio 2017 and VSTS Git (Freigeben von Code mit Visual Studio 2017 und VSTS Git)](https://docs.microsoft.com/vsts/git/share-your-code-in-git-vs-2017).


## <a name="tutorial-review"></a>Review des Tutorials

Glückwunsch zum Abschluss dieses Tutorials zu Python in Visual Studio. In diesem Tutorial haben Sie Folgendes gelernt:

- Erstellen von Projekten und Anzeigen der Projektinhalte
- Verwenden des Code-Editors und Ausführen eines Projekts
- Verwenden Sie das interaktive Fenster, um neuen Code zu entwickeln und diesen einfach in den Editor zu kopieren.
- Führen Sie ein abgeschlossenes Programm im Visual Studio-Debugger aus.
- Installieren von Paketen und Verwalten von Python-Umgebungen
- Arbeiten mit Code in einem Git-Repository

Erkunden Sie nun unter anderem folgende Konzepte und Leitfäden:

- [Erstellen einer C++-Erweiterung für Python](cpp-and-python.md)
- [Veröffentlichen in Azure App Service](publishing-to-azure.md)
- [Profilerstellung](profiling.md)
- [Komponententests](unit-testing.md)
