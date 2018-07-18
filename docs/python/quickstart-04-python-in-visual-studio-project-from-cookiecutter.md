---
title: 'Schnellstart: Erstellen eines Python-Projekts mithilfe von Cookiecutter'
description: In diesem Schnellstart erstellen Sie ein Visual Studio-Projekt für Python mithilfe einer Cookiecutter-Vorlage.
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: daaeefc8dcefecf035a70989d206564ca84bf198
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956944"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Schnellstart: Erstellen eines Python-Projekts aus einer Cookiecutter-Vorlage

Sobald Sie die [Python-Unterstützung in Visual Studio 2017 installiert haben](installing-python-support-in-visual-studio.md), können Sie ganz einfach ein neues Projekt aus einer Cookiecutter-Vorlage erstellen. Viele dieser Vorlagen wurden bereits auf GitHub veröffentlicht. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) stellt eine grafische Benutzeroberfläche bereit, auf der Sie Vorlagen ermitteln, Vorlageoptionen eingeben und Projekte und Dateien erstellen können. Die Erweiterung ist im Lieferumfang von Visual Studio 2017 enthalten und kann separat in früheren Versionen von Visual Studio installiert werden.

1. Installieren Sie für diesen Schnellstart zuerst die Python-Verteilung Anaconda3. Sie enthält die erforderlichen Python-Pakete für die hier gezeigte Cookiecutter-Vorlage. Führen Sie den Visual Studio-Installer aus, klicken Sie auf **Ändern**, erweitern Sie rechts die Optionen für **Python-Entwicklung**, und wählen Sie „Anaconda3“ aus (32-Bit oder 64-Bit). Die Installation kann je nach Geschwindigkeit Ihres Internets einige Zeit in Anspruch nehmen. Dies ist jedoch der einfachste Weg, die erforderlichen Pakete zu installieren.

1. Starten Sie Visual Studio.

1. Klicken Sie auf **Datei > Neu > Aus Cookiecutter…**. Mit diesem Befehl wird ein Fenster in Visual Studio geöffnet, in dem Sie Vorlagen durchsuchen können. 

    ![Neues Projekt aus einer Cookiecutter-Vorlage erstellen](media/projects-from-cookiecutter1.png)

1. Wenn Sie die Vorlage „Microsoft/python-sklearn-classifier-cookiecutter“ ausgewählt haben, klicken Sie auf **Weiter**. Dieser Prozess kann bei der ersten Verwendung von Cookiecutter mehrere Minuten dauern.

1. Legen Sie als Nächstes über das Feld **Erstellen in** einen Speicherort für das neue Projekt fest, und klicken Sie dann auf **Erstellen**.

    ![Zweiter Schritt mit Cookiecutter, Festlegen von Projekteigenschaften](media/projects-from-cookiecutter2.png)

1. Wenn der Prozess abgeschlossen ist, sehen Sie die Meldung „Files created successfully“ (Die Dateien wurden erfolgreich erstellt). Klicken Sie auf den Befehl **Im Projektmappen-Explorer öffnen**, um das Projekt zu öffnen.

1. Drücken Sie STRG+F5, oder klicken Sie auf **Debuggen > Ohne Debuggen starten**, um das Programm auszuführen. 

    ![Ausgabe des Vorlagenprojekts „python-sklearn-classifier-cookiecutter“](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Tutorial: Arbeiten mit Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Siehe auch

- [Verwenden der Cookiecutter-Erweiterung](using-python-cookiecutter-templates.md)
- [Manuelles Identifizieren eines vorhandenen Python-Interpreters](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Installieren der Python-Unterstützung für Visual Studio 2015 und früher](installing-python-support-in-visual-studio.md)
- [Installationsspeicherorte](installing-python-support-in-visual-studio.md#install-locations)
