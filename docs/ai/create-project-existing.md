---
title: Erstellen eines KI-Projekts aus vorhandenem Code
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.service: multiple
ms.workload:
- multiple
ms.openlocfilehash: a2a09fd3214cddf4f63fd2c32874db5b67a9b9dc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760438"
---
# <a name="create-an-ai-project-from-existing-code"></a>Erstellen eines KI-Projekts aus vorhandenem Code

Sobald Sie [die Visual Studio-Tools für KI installiert haben](installation.md), können Sie ganz leicht vorhandenen Python-Code einem Visual Studio-Projekt hinzufügen.

> [!Important]
> Der hier beschriebene Prozess verschiebt oder kopiert die ursprünglichen Quelldateien nicht. Wenn Sie mit einer Kopie arbeiten möchten, erstellen Sie zunächst eine Kopie des Ordners.

1. Starten Sie Visual Studio, und wählen Sie **Datei > Neu > Projekt** aus.

2. Suchen Sie im Dialogfeld **Neues Projekt** nach **KI-Tools**. Wählen Sie die Vorlage **Aus vorhandenem Python-Code** aus, legen Sie für das Projekt einen Namen und einen Speicherort fest, und klicken Sie anschließend auf **OK**.

   ![Neues Projekt aus vorhandenem Code – Schritt 1](media/create-project-existing/new-ai-project.png)

3. Legen Sie im Assistenten, der angezeigt wird, den Pfad zu Ihrem vorhandenen Code und einen Filter für Dateitypen fest, geben Sie Suchpfade an, die das Projekt benötigt, und klicken Sie auf **OK**. Wenn Sie nicht wissen, was Suchpfade sind, lassen Sie das Feld leer.

   ![Neues Projekt aus vorhandenem Code – Schritt 2](media/create-project-existing/azurebatch-newproject.png)

   Wenn Ihr vorhandener Code Teil eines Azure Machine Learning-Projekts ist, überprüfen Sie den Ordner **Is Azure Machine Learning**, um eine erfolgreiche Konvertierung wichtiger Azure Machine Learning-Konfigurationsdetails zu gewährleisten, wie z.B. Experimentierkonto, Arbeitsbereich, zu verwendende Computekontexte und mehr.

4. Um eine Startdatei festzulegen, suchen Sie die Datei im **Projektmappen-Explorer**. Klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Als Startdatei festlegen** aus.

5. Führen Sie das Programm durch Drücken von **STRG**+**F5** oder Auswählen von **Debuggen > Starten ohne Debuggen** aus.

> [!div class="nextstepaction"]
> [Tutorial: Arbeiten mit Python in Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Siehe auch

- [Manuelles Identifizieren einer vorhandenen Python-Umgebung](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)