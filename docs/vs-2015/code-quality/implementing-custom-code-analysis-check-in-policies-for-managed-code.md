---
title: Implementieren von benutzerdefiniertem Code Codeanalyse-Eincheckrichtlinien für verwalteten Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f0b22eabc4df4b6ce7e8596f0c6546cb3a4c61c8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696655"
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementieren von benutzerdefinierten Eincheckrichtlinien für die Codeanalyse für verwalteten Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Codeanalyse-Eincheckrichtlinie gibt einen Satz von Regeln an, die Mitglieder eines Teamprojekts im Quellcode ausgeführt werden müssen, bevor sie die Versionskontrolle eingecheckt ist. Microsoft bietet eine Reihe von *-Regelsätze* dieser Gruppe Codeanalyseregeln in mehrere Funktionsbereiche. *Benutzerdefinierte Eincheckrichtlinien-Regelsätze* Geben Sie einen Satz von Codeanalyseregeln, die für ein Teamprojekt spezifisch sind. Ein Regelsatz wird in eine RULESET-Datei gespeichert.  
  
 Check-in-Richtlinien werden auf Teamprojektebene festgelegt und durch den Speicherort des eine RULESET-Datei in der Steuerelementstruktur Version angegeben. Es gibt keine Einschränkungen für den Speicherort der Versionskontrolle von der Team-Richtliniensatz benutzerdefinierte Regel.  
  
 Die Codeanalyse ist für die einzelne Codeprojekte im Fenster "Eigenschaften" für jedes Projekt konfiguriert. Eine benutzerdefinierte Regel für ein Codeprojekt wird durch den physischen Speicherort der RULESET-Datei auf dem lokalen Computer angegeben. Wenn eine RULESET-Datei angegeben wird, auf dem gleichen Laufwerk wie das Codeprojekt befindet, verwendet Visual Studio einen relativen Pfad in die Datei in der Projektkonfiguration.  
  
 Eine mögliche Vorgehensweise zum Erstellen eines Team-Projekt des benutzerdefinierten Regelsatzes ist der Eincheckrichtlinie RULESET-Datei in einem speziellen Ordner zu speichern, die nicht Teil jedes Codeprojekt ist. Wenn Sie die Datei in einem dedizierten Ordner speichern, können Sie die Berechtigungen, die beschränken, die die Regeldatei bearbeiten können anwenden können Sie die Verzeichnisstruktur problemlos wechseln enthält, das Projekt zu einem anderen Verzeichnis oder Computer.  
  
## <a name="creating-the-team-project-custom-check-in-rule-set"></a>Den Team-Projekt benutzerdefinierte Einchecken Regelsatz erstellen  
 Um eine benutzerdefinierte Regel für ein Teamprojekt zu erstellen, Sie für den Regelsatz-Eincheckrichtlinie einen speziellen Ordner zuerst erstellen **Quellcodeverwaltungs-Explorer**. Dann erstellen die Regelsatzdatei und fügen Sie die Datei zur Versionskontrolle hinzu. Abschließend geben Sie den Regelsatz, der als das Einchecken Codeanalyserichtlinie für das Teamprojekt.  
  
> [!NOTE]
> Um einen Ordner in einem Teamprojekt zu erstellen, müssen Sie zuerst das Stammverzeichnis des Projekts Team an einem Speicherort auf dem lokalen Computer zuordnen. Weitere Informationen finden Sie unter [erstellen und Verwenden von Arbeitsbereichen (ALT)](https://msdn.microsoft.com/db4d5692-179a-44fe-ad31-0c1c900c9cb2).  
  
#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Erstellen Sie den Versionskontrollordner für den Regelsatz-Eincheckrichtlinie  
  
1. In [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], erweitern Sie den Team-Projektknoten, und klicken Sie dann auf **Quellcodeverwaltung**.  
  
2. In der **Ordner** Bereich mit der rechten Maustaste in des Teamprojekts, und klicken Sie dann auf **neuer Ordner**.  
  
3. Die Datenquellen-Steuerelement im Hauptbereich, mit der Maustaste **neuer Ordner**, klicken Sie auf **umbenennen**, und geben Sie einen Namen für den Regelsatz-Ordner.  
  
#### <a name="to-create-the-check-in-policy-rule-set"></a>Legen Sie zum Erstellen der Regel-Eincheckrichtlinie  
  
1. Auf der **Datei** Startmenü **neu**, und klicken Sie dann auf **Datei**.  
  
2. In der **Kategorien** auf **allgemeine**.  
  
3. In der **Vorlagen** auflisten, doppelklicken Sie auf **Codeanalyse-Regelsatz**.  
  
4. Angeben von Regeln, in dem Regelsatz aktiviert sind, und speichern Sie die Regelsatzdatei in der Regel Satz-Ordner, die Sie erstellt haben.  
  
     Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### <a name="to-add-the-rule-set-file-to-version-control"></a>Hinzufügen die Regel legen Datei zur Versionskontrolle  
  
1. In **Quellcodeverwaltungs-Explorer**mit der rechten Maustaste auf den neuen Ordner, und klicken Sie dann auf **Elemente zu Ordner hinzufügen**.  
  
     Weitere Informationen finden Sie unter [verwenden der Versionskontrolle](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314).  
  
2. Klicken Sie auf den Regelsatz-Datei, die Sie erstellt haben, und klicken Sie dann auf **Fertig stellen**.  
  
     Die Datei zur quellcodeverwaltung hinzugefügt und für Sie ausgecheckt.  
  
3. In der **Quellcodeverwaltungs-Explorer** Fenster "Klassendetails", mit der rechten Maustaste in des Dateinamens, und klicken Sie dann auf **ausstehende Änderungen einchecken**.  
  
4. In der **Einchecken** (Dialogfeld), Sie haben die Option zum Hinzufügen eines Kommentars, und klicken Sie dann auf **Einchecken**.  
  
    > [!NOTE]
    > Wenn Sie eine Eincheckrichtlinie für die Analyse bereits für das Teamprojekt konfiguriert haben, und Sie ausgewählt haben die **erzwingen, um nur die Dateien enthalten, die Teil der aktuellen Projektmappe eingecheckt**, Sie löst eine Warnung zu Fehler bei Richtlinie. Wählen Sie in das Dialogfeld Richtlinienfehler **Richtlinienfehler überschreiben und organg fortsetzen**. Hinzufügen eines Kommentars erforderliches, und klicken Sie dann auf **OK**.  
  
#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Legen die Regel an Datei als die Check-in-Richtlinie  
  
1. Auf der **Team** Startmenü **Teamprojekteinstellungen**, und klicken Sie dann auf **Quellcodeverwaltung**.  
  
2. Klicken Sie auf **Eincheckrichtlinie**, und klicken Sie dann auf **hinzufügen**.  
  
3. In der **Eincheckrichtlinie** auflisten, doppelklicken Sie auf **Codeanalyse**, und stellen Sie sicher, dass die **Codeanalyse für verwalteten Code erzwingen** das Kontrollkästchen aktiviert ist.  
  
4. In der **diesen Regelsatz ausführen** auf  **\<Regelsatz auswählen aus der Quellcodeverwaltung >**.  
  
5. Geben Sie den Pfad der Regeldatei Satz Eincheckrichtlinie, in der Versionskontrolle.  
  
     Der Pfad muss mit der folgenden Syntax entsprechen:  
  
     **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    > [!NOTE]
    > Kopieren Sie den Pfad, indem Sie eine der folgenden Verfahren in **Quellcodeverwaltungs-Explorer**:  
  
    - In der **Ordner** Bereich, klicken Sie auf den Ordner, die Regelsatzdatei enthält. Kopieren Sie den Versionskontrollpfad des Ordners, der angezeigt wird der **Quelle** Feld, und geben Sie den Namen des der Regelsatzdatei manuell.  
  
    - Im Detailfenster mit der Maustaste der Regelsatzdatei, und klicken Sie dann auf **Eigenschaften**. Auf der **allgemeine** Registerkarte, kopieren Sie den Wert in **Servernamen**.  
  
## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>Synchronisieren der Codeprojekte den Regelsatz-Eincheckrichtlinie  
 Sie geben Sie eine Team Project-Eincheckrichtlinie Regel als die Codeanalyse-Regelsatz mit einer Projektkonfiguration für Code in das Dialogfeld "Eigenschaften" des Codeprojekts festlegen. Wenn der Regelsatz auf dem gleichen Laufwerk wie der Codeprojekt befindet, wird ein relativer Pfad verwendet, Regelsatz an, wenn der Pfad im Dialogfeld "Datei" ausgewählt ist. Der relative Pfad ermöglicht es den projekteinstellungen für die Eigenschaften auf anderen Computern übertragbar, die ähnlich wie lokalen Version verwenden Steuerungsstrukturen.  
  
#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>An einem Teamprojekt-Regelsatz, der als dem Regelsatz eines Codeprojekts festlegen  
  
1. Rufen Sie ggf. die Eincheckrichtlinie Regel der Ordner "Set" und die Datei aus der Versionskontrolle.  
  
     Sie können diesen Schritt ausführen **Quellcodeverwaltungs-Explorer** durch Rechtsklick auf die Regel festgelegt, Ordner und klicken Sie dann auf **neuste Version abrufen**.  
  
2. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Codeprojekt, und klicken Sie dann auf **Eigenschaften**.  
  
3. **Klicken Sie auf Codeanalyse**.  
  
4. Klicken Sie ggf. auf die entsprechenden Optionen in der **Konfiguration** und **Plattform** aufgeführt.  
  
5. Um die Analyse von Code jedes Mal ausführen, die den Codeprojekt mit der angegebenen Konfiguration erstellt wird, wählen Sie die **Codeanalyse für Build aktivieren (definiert eine CODE_ANALYSIS-Konstante)** Kontrollkästchen.  
  
6. Wenn Code in Komponenten von anderen Unternehmen ignorieren möchten, wählen Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.  
  
7. In der **diesen Regelsatz ausführen** auf  **\<durchsuchen... >**.  
  
8. Geben Sie die lokale Version der Regelsatzdatei der Eincheckrichtlinie.
