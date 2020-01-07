---
title: Eincheck Richtlinien für benutzerdefinierte Code Analyse für verwalteten Code
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9386d89ce995131bdb89f94201fa8475058ddba0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587393"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementieren von benutzerdefinierten Eincheckrichtlinien für die Codeanalyse für verwalteten Code

Eincheckrichtlinie für die Analyse gibt einen Satz von Regeln, die Mitglieder eines Azure DevOps-Projekts im Quellcode ausgeführt werden müssen, bevor sie die Versionskontrolle eingecheckt ist. Microsoft bietet eine Reihe von *-Regelsätze* dieser Gruppe Codeanalyseregeln in mehrere Funktionsbereiche. *Benutzerdefinierte Eincheckrichtlinien-Regelsätze* Geben Sie einen Satz von Codeanalyseregeln, die für ein Projekt spezifisch sind. Ein Regelsatz wird in eine RULESET-Datei gespeichert.

Check-in-Richtlinien sind der Ebene des Azure DevOps-Projekts festgelegt und durch den Speicherort des eine RULESET-Datei in der Steuerelementstruktur Version angegeben. Es gibt keine Einschränkungen für den Speicherort der Versionskontrolle von der Team-Richtliniensatz benutzerdefinierte Regel.

Die Codeanalyse ist für die einzelne Codeprojekte im Fenster "Eigenschaften" für jedes Projekt konfiguriert. Eine benutzerdefinierte Regel für ein Codeprojekt wird durch den physischen Speicherort der RULESET-Datei auf dem lokalen Computer angegeben. Wenn eine RULESET-Datei angegeben wird, auf dem gleichen Laufwerk wie das Codeprojekt befindet, verwendet Visual Studio einen relativen Pfad in die Datei in der Projektkonfiguration.

Eine mögliche Vorgehensweise zum Erstellen einer Azure DevOps-Projekt benutzerdefinierte Regel ist die Eincheckrichtlinie RULESET-Datei in einem speziellen Ordner zu speichern, die nicht Teil jedes Codeprojekt ist. Wenn Sie die Datei in einem dedizierten Ordner speichern, können Sie die Berechtigungen, die beschränken, die die Regeldatei bearbeiten können anwenden können Sie die Verzeichnisstruktur problemlos wechseln enthält, das Projekt zu einem anderen Verzeichnis oder Computer.

## <a name="create-the-project-custom-check-in-rule-set"></a>Erstellen Sie den Projekt benutzerdefinierten Einchecken Regelsatz

Um eine benutzerdefinierte Regel für ein Azure DevOps-Projekt zu erstellen, Sie für den Regelsatz-Eincheckrichtlinie einen speziellen Ordner zuerst erstellen **Quellcodeverwaltungs-Explorer**. Dann erstellen die Regelsatzdatei und fügen Sie die Datei zur Versionskontrolle hinzu. Abschließend geben Sie die Regel als das Einchecken Codeanalyserichtlinie für das Projekt festlegen.

> [!NOTE]
> Um einen Ordner in einem Azure DevOps-Projekt zu erstellen, müssen Sie zuerst das Stammverzeichnis des Projekts an einem Speicherort auf dem lokalen Computer zuordnen.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Erstellen Sie den Versionskontrollordner für den Regelsatz-Eincheckrichtlinie

1. Klicken Sie in Team Explorer, erweitern Sie den Projektknoten, und klicken Sie dann auf **Quellcodeverwaltung**.

2. In der **Ordner** Bereich mit der rechten Maustaste in des Projekts, und klicken Sie dann auf **neuer Ordner**.

3. Die Datenquellen-Steuerelement im Hauptbereich, mit der Maustaste **neuer Ordner**, klicken Sie auf **umbenennen**, und geben Sie einen Namen für den Regelsatz-Ordner.

### <a name="to-create-the-check-in-policy-rule-set"></a>Legen Sie zum Erstellen der Regel-Eincheckrichtlinie

1. Auf der **Datei** Startmenü **neu**, und klicken Sie dann auf **Datei**.

2. In der **Kategorien** auf **allgemeine**.

3. In der **Vorlagen** auflisten, doppelklicken Sie auf **Codeanalyse-Regelsatz**.

4. [Geben Sie die Regeln](../code-quality/how-to-create-a-custom-rule-set.md) legen Sie in dem Regelsatz aktiviert, und speichern Sie den Regelsatz-Datei auf den Regelsatzordner, die Sie erstellt haben.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Hinzufügen die Regel legen Datei zur Versionskontrolle

1. In **Quellcodeverwaltungs-Explorer**mit der rechten Maustaste auf den neuen Ordner, und klicken Sie dann auf **Elemente zu Ordner hinzufügen**.

     Weitere Informationen finden Sie unter [Git und Azure-Repositorys](/azure/devops/repos/git/overview?view=vsts).

2. Klicken Sie auf den Regelsatz-Datei, die Sie erstellt haben, und klicken Sie dann auf **Fertig stellen**.

     Die Datei zur quellcodeverwaltung hinzugefügt und für Sie ausgecheckt.

3. In der **Quellcodeverwaltungs-Explorer** Fenster "Klassendetails", mit der rechten Maustaste in des Dateinamens, und klicken Sie dann auf **ausstehende Änderungen einchecken**.

4. In der **Einchecken** (Dialogfeld), Sie haben die Option zum Hinzufügen eines Kommentars, und klicken Sie dann auf **Einchecken**.

    > [!NOTE]
    > Wenn Sie eine Eincheckrichtlinie für die Analyse bereits für das Azure DevOps-Projekt konfiguriert haben, und Sie ausgewählt haben, die **erzwingen, um nur die Dateien enthalten, die Teil der aktuellen Projektmappe eingecheckt**, Sie löst eine Warnung: Richtlinie. Wählen Sie in das Dialogfeld Richtlinienfehler **Richtlinienfehler überschreiben und organg fortsetzen**. Hinzufügen eines Kommentars erforderliches, und klicken Sie dann auf **OK**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Legen die Regel an Datei als die Check-in-Richtlinie

1. Auf der **Team** Startmenü **Projekteinstellungen**, und klicken Sie dann auf **Quellcodeverwaltung**.

2. Klicken Sie auf **Eincheckrichtlinie**, und klicken Sie dann auf **hinzufügen**.

3. In der **Eincheckrichtlinie** auflisten, doppelklicken Sie auf **Codeanalyse**, und stellen Sie sicher, dass die **Codeanalyse für verwalteten Code erzwingen** das Kontrollkästchen aktiviert ist.

4. In der **diesen Regelsatz ausführen** auf  **\<Regelsatz auswählen aus der Quellcodeverwaltung >** .

5. Geben Sie den Pfad der Regeldatei Satz Eincheckrichtlinie, in der Versionskontrolle.

     Der Pfad muss mit der folgenden Syntax entsprechen:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Kopieren Sie den Pfad, indem Sie eine der folgenden Verfahren in **Quellcodeverwaltungs-Explorer**:

    - In der **Ordner** Bereich, klicken Sie auf den Ordner, die Regelsatzdatei enthält. Kopieren Sie den Versionskontrollpfad des Ordners, der angezeigt wird der **Quelle** Feld, und geben Sie den Namen des der Regelsatzdatei manuell.

    - Im Detailfenster mit der Maustaste der Regelsatzdatei, und klicken Sie dann auf **Eigenschaften**. Auf der **allgemeine** Registerkarte, kopieren Sie den Wert in **Servernamen**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Synchronisieren der Codeprojekte den Regelsatz-Eincheckrichtlinie

Sie geben Sie eine Regel des Project-Eincheckrichtlinie als die Codeanalyse-Regelsatz mit einer Projektkonfiguration für Code in das Dialogfeld "Eigenschaften" des Codeprojekts festgelegt. Wenn der Regelsatz auf dem gleichen Laufwerk wie der Codeprojekt befindet, wird ein relativer Pfad verwendet, Regelsatz an, wenn der Pfad im Dialogfeld "Datei" ausgewählt ist. Der relative Pfad ermöglicht es den projekteinstellungen für die Eigenschaften auf anderen Computern übertragbar, die ähnlich wie lokalen Version verwenden Steuerungsstrukturen.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>Eine Projekt-Regel angeben, die als dem Regelsatz eines Codeprojekts festlegen

1. Rufen Sie ggf. die Eincheckrichtlinie Regel der Ordner "Set" und die Datei aus der Versionskontrolle.

   Sie können diesen Schritt ausführen **Quellcodeverwaltungs-Explorer** durch Rechtsklick auf die Regel festgelegt, Ordner und klicken Sie dann auf **neuste Version abrufen**.

2. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Codeprojekt, und klicken Sie dann auf **Eigenschaften**.

3. **Klicken Sie auf Codeanalyse**.

4. Klicken Sie ggf. auf die entsprechenden Optionen in der **Konfiguration** und **Plattform** aufgeführt.

::: moniker range="vs-2017"

5. Wenn Sie die Code Analyse bei jedem Erstellen des Code Projekts mithilfe der angegebenen Konfiguration ausführen möchten, wählen Sie **Code Analyse beim Build aktivieren aus**.

::: moniker-end

::: moniker range=">=vs-2019"

5. Um die Code Analyse jedes Mal auszuführen, wenn das Code Projekt mithilfe der angegebenen Konfiguration erstellt wird, wählen Sie im Abschnitt **binäre Analysen** die Option **im Build ausführen** aus.

::: moniker-end

6. Klicken Sie in der Liste **diesen Regelsatz ausführen** auf **\<Durchsuchen >** .

8. Wählen Sie die lokale Version der Regel Satz Datei für die Eincheck Richtlinie aus.
