---
title: Implementieren von benutzerdefiniertem Code Analysis-Eincheckrichtlinien für verwalteten Code in Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c60c682fe4613495a90b78c47189dc6b84b38399
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923549"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementieren von benutzerdefiniertem Code Analysis-Eincheckrichtlinien für verwalteten Code

Die Codeanalyse in der Eincheckrichtlinie für einen Satz von Regeln gibt, die Mitglieder eines Teamprojekts für den Quellcode ausführen müssen, bevor er in die Versionskontrolle eingecheckt wird. Microsoft bietet eine Reihe von *-Regelsätze* dieser Gruppe Codeanalyse Regeln in Funktionsbereiche. *Benutzerdefinierte Eincheckrichtlinie Regelsätze* Geben Sie einen Satz von Codeanalyseregeln, die für ein Teamprojekt spezifisch sind. Ein Regelsatz wird in eine RULESET-Datei gespeichert.

Eincheckrichtlinien werden auf Teamprojektebene festgelegt und von der Position des RULESET-Datei in der Konsolenstruktur Version angegeben. Es gibt keine Einschränkungen auf den Speicherort der Versionskontrolle des Satzes Team Richtlinie benutzerdefinierte Regel.

Codeanalyse ist für die einzelnen Codeprojekte im Eigenschaftenfenster für jedes Projekt konfiguriert. Ein benutzerdefiniertes Regelsatzes für ein Codeprojekt wird durch den physischen Speicherort der RULESET-Datei auf dem lokalen Computer angegeben. Wenn eine RULESET-Datei angegeben ist, auf dem gleichen Laufwerk wie das Codeprojekt befindet, verwendet Visual Studio einen relativen Pfad zur Datei in der Projektkonfiguration.

Eine mögliche Vorgehensweise zum Erstellen eines Teams Projekt des benutzerdefinierten Regelsatzes besteht darin, in der Eincheckrichtlinie RULESET-Datei in einem speziellen Ordner zu speichern, die nicht Teil eines Codeprojekts ist. Wenn Sie die Datei in einen dedizierten Ordner speichern, Sie die Berechtigungen, die einschränken, wer Regeldatei bearbeiten können anwenden und können Sie die Verzeichnisstruktur problemlos verschieben enthält, das Projekt zu einem anderen Verzeichnis oder Computer können.

## <a name="create-the-team-project-custom-check-in-rule-set"></a>Erstellen der Team Project benutzerdefinierten Eincheckvorgangs Regelsatzes

Zum Erstellen eines benutzerdefinierten Regelsatzes für ein Teamprojekt erstellen Sie zunächst einen besonderen Ordner für die Eincheckrichtlinie Regelsatz in **Quellcodeverwaltungs-Explorer**. Klicken Sie dann die Regelsatzdatei erstellen und die Datei zur Versionskontrolle hinzufügen. Geben Sie schließlich den Regelsatz als die Eincheckvorgangs Codeanalyserichtlinie für das Teamprojekt an.

> [!NOTE]
> Um einen Ordner in einem Teamprojekt zu erstellen, müssen Sie zuerst die Teamprojektstamm an einen Speicherort auf dem lokalen Computer zuordnen.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>So erstellen Ordner für den Regelsatz in der Eincheckrichtlinie für die Versionskontrolle

1. Klicken Sie in Team Explorer, erweitern Sie den Teamprojektknoten, und klicken Sie dann auf **Quellcodeverwaltung**.

2. In der **Ordner** Bereich mit der rechten Maustaste in des Teamprojekts, und klicken Sie dann auf **neuer Ordner**.

3. Im Hauptbereich des Datenquellen-Steuerelements mit der Maustaste **neuer Ordner**, klicken Sie auf **umbenennen**, und geben Sie einen Namen für die Regel Ordner festgelegt werden.

### <a name="to-create-the-check-in-policy-rule-set"></a>So erstellen den Regelsatz-Eincheckrichtlinie

1. Auf der **Datei** Sie im Menü **neu**, und klicken Sie dann auf **Datei**.

2. In der **Kategorien** auf **allgemeine**.

3. In der **Vorlagen** auflisten, doppelklicken Sie auf **Codeanalyse-Regelsatz**.

4. [Geben Sie die Regeln](../code-quality/how-to-create-a-custom-rule-set.md) im Regelsatz, und speichern Sie die Regel Regelsatzdatei auf von Ihnen erstellten Ordner für die Regel festlegen.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Hinzufügen die Regel legen Datei zur Versionskontrolle

1. In **Quellcodeverwaltungs-Explorer**mit der rechten Maustaste auf den neuen Ordner, und klicken Sie dann auf **Elemente hinzufügen, um den Ordner**.

     Weitere Informationen finden Sie unter [Git und der VSTS](/vsts/git/overview).

2. Klicken Sie auf den Regelsatz-Datei, die Sie erstellt haben, und klicken Sie dann auf **Fertig stellen**.

     Die Datei wird zur quellcodeverwaltung hinzugefügt und für Sie ausgecheckt.

3. In der **Quellcodeverwaltungs-Explorer** Fenster "Klassendetails", mit der rechten Maustaste in des Dateinamens, und klicken Sie dann auf **ausstehenden Änderungen einchecken**.

4. In der **Einchecken** (Dialogfeld), haben Sie die Möglichkeit, einen Kommentar hinzufügen, und klicken Sie dann auf **Einchecken**.

    > [!NOTE]
    > Wenn eine Eincheckrichtlinie für die Analyse für das Teamprojekt bereits konfiguriert haben und Sie ausgewählt haben, die **erzwingen Check-in, um nur die Dateien enthalten, die Teil der aktuellen Projektmappe sind**, Sie löst eine Warnung der Richtlinie:. Wählen Sie im Dialogfeld Richtlinienfehler **Richtlinienfehler und Einchecken Fortfahren**. Hinzufügen eines Kommentars erforderliches, und klicken Sie dann auf **OK**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Die Regel an Regelsatzdatei als der Eincheckrichtlinie

1. Auf der **Team** Sie im Menü **Teamprojekteinstellungen**, und klicken Sie dann auf **Quellcodeverwaltung**.

2. Klicken Sie auf **Eincheckrichtlinie**, und klicken Sie dann auf **hinzufügen**.

3. In der **Eincheckrichtlinie** auflisten, doppelklicken Sie auf **Codeanalyse**, und stellen Sie sicher, dass die **Codeanalyse für verwalteten Code erzwingen** Kontrollkästchen aktiviert ist.

4. In der **diesen Regelsatz ausführen** auf  **\<aus der Quellcodeverwaltung Regelsatz auswählen >**.

5. Geben Sie den Pfad der Regeldatei Satz Eincheckrichtlinie in der Versionskontrolle.

     Der Pfad muss mit der folgenden Syntax entsprechen:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Kopieren Sie den Pfad mit einer der folgenden Verfahren in **Quellcodeverwaltungs-Explorer**:

    - In der **Ordner** Bereich, klicken Sie auf den Ordner, der die Regelsatzdatei enthält. Kopieren den Versionskontrollpfad des Ordners, der in der **Quelle** Feld, und geben Sie den Namen der Regelsatzdatei manuell.

    - Im Detailfenster mit der Maustaste der Regelsatzdatei, und klicken Sie dann auf **Eigenschaften**. Auf der **allgemeine** Registerkarte, kopieren Sie den Wert in **Servernamen**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Synchronisieren der Codeprojekte zum Regelsatz für die Eincheckrichtlinie

Sie geben Sie ein Teamprojekt-Eincheckrichtlinie Regelsatz als die Codeanalyse-Regelsatz einer Projektkonfiguration Code im Dialogfeld "Eigenschaften" des Codeprojekts gesetzt. Der Regelsatz auf dem gleichen Laufwerk wie das Codeprojekt befindet, wird ein relativer Pfad zum Regelsatz anzugeben, wenn der Pfad von Dateidialogfeld ausgewählt ist. Der relative Pfad ermöglicht es die eigenschafteneinstellungen des Projekts auf anderen Computern übertragbar, mit denen ähnliche lokale Version Steuerelementstrukturen.

### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Legen Sie an einem Teamprojekt-Regelsatz als Regelsatz ein Codeprojekt

1. Bei Bedarf abgerufen Sie werden die in der Eincheckrichtlinie Regelsatzordner und die Datei in der Versionskontrolle.

   Sie können in diesem Schritt führen Sie **Quellcodeverwaltungs-Explorer** durch Rechtsklick auf die Regel festgelegt, Ordner, und klicken Sie dann auf **neuste Version abrufen**.

2. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Codeprojekt, und klicken Sie dann auf **Eigenschaften**.

3. **Klicken Sie auf die Codeanalyse**.

4. Klicken Sie ggf. auf die entsprechenden Optionen in der **Konfiguration** und **Plattform** aufgeführt.

5. Um die Codeanalyse jedes Mal ausgeführt, die den Codeprojekt mit der angegebenen Konfiguration erstellt wird, wählen Sie die **Codeanalyse für Build aktivieren (definiert eine CODE_ANALYSIS-Konstante)** Kontrollkästchen.

6. Wenn Code in Komponenten von anderen Unternehmen ignorieren möchten, wählen Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.

7. In der **diesen Regelsatz ausführen** auf  **\<durchsuchen... >**.

8. Geben Sie die lokale Version der Regeldatei Satz in der Eincheckrichtlinie.