---
title: "Implementieren von benutzerdefinierten Eincheckrichtlinien f&#252;r die Codeanalyse f&#252;r verwalteten Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.code.analysis.selecttfsrulesets"
  - "vs.code.analysis.browsefortfsruleset"
  - "vs.code.analysis.policyeditor"
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Implementieren von benutzerdefinierten Eincheckrichtlinien f&#252;r die Codeanalyse f&#252;r verwalteten Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit einer Eincheckrichtlinie für die Codeanalyse wird ein Satz von Regeln angegeben, den die Mitglieder eines Teamprojekts für Quellcode ausführen müssen, bevor dieser in die Versionskontrolle eingecheckt wird.  Von Microsoft wird eine Gruppe von *Standardregelsätzen* bereitgestellt, mit denen die Codeanalyseregeln in Funktionsbereiche gruppiert werden.  Mit *benutzerdefinierten Eincheckrichtlinien\-Regelsätzen* wird ein Satz von teamprojektspezifischen Codeanalyseregeln angegeben.  Regelsätze werden in einer RULESET\-Datei gespeichert.  
  
 Eincheckrichtlinien werden auf Teamprojektebene festgelegt und anhand des Speicherorts einer RULESET\-Datei in der Versionskontrollstruktur angegeben.  Für den Versionskontrollspeicherort des benutzerdefinierten Teamprojekt\-Regelsatzes bestehen keinerlei Einschränkungen.  
  
 Die Codeanalyse wird im Eigenschaftenfenster des jeweiligen Projekts für die einzelnen Codeprojekte konfiguriert.  Ein benutzerdefinierter Regelsatz für ein Codeprojekt wird anhand des physikalischen Speicherorts der RULESET\-Datei auf dem lokalen Computer angegeben.  Wird eine RULESET\-Datei angegeben, die auf dem gleichen Laufwerk wie das Codeprojekt, wird Visual Studio einen relativen Dateipfad in der Projektkonfiguration.  
  
 Eine mögliche Vorgehensweise zum Erstellen eines benutzerdefinierten Teamprojekt\-Regelsatzes ist, die Eincheckrichtliniendatei \(RULESET\-Datei\) in einem speziellen Ordner zu speichern, der nicht Teil eines Codeprojekts ist.  Wenn Sie die Datei in einem dedizierten Ordner speichern, können Sie Berechtigungen anwenden, um die Bearbeitung der Regeldatei durch bestimmte Personen einzuschränken. Darüber hinaus kann die Verzeichnisstruktur mit dem Projekt problemlos in ein anderes Verzeichnis oder auf einen anderen Computer verschoben werden.  
  
## Erstellen des benutzerdefinierten Teamprojekt\-Eincheckregelsatzes  
 Zum Erstellen eines benutzerdefinierten Regelsatzes für ein Teamprojekt muss im Quellcodeverwaltungs\-Explorer zunächst ein spezieller Ordner für die Eincheckrichtlinienregel erstellt werden.  Anschließend wird die Regelsatzdatei erstellt und der Versionskontrolle hinzugefügt.  Und schließlich wird der Regelsatz als Codeanalyse\-Eincheckrichtlinie für das Teamprojekt angegeben.  
  
> [!NOTE]
>  Damit Sie in einem Teamprojekt einen Ordner erstellen können, muss zunächst der Teamprojektstamm einem Speicherort auf dem lokalen Computer zugeordnet werden.  Weitere Informationen finden Sie unter [Create and work with workspaces \(old\)](http://msdn.microsoft.com/de-de/db4d5692-179a-44fe-ad31-0c1c900c9cb2).  
  
#### So erstellen Sie den Versionskontrollordner für den Eincheckrichtlinien\-Regelsatz  
  
1.  Erweitern Sie in [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] den Teamprojektknoten, und klicken Sie anschließend auf **Quellcodeverwaltung**.  
  
2.  Klicken Sie im Bereich **Ordner** mit der rechten Maustaste auf das Teamprojekt, und klicken Sie anschließend auf **Neuer Ordner**.  
  
3.  Klicken Sie im Bereich "Quellcodesteuerung" mit der rechten Maustaste auf **Neuer Ordner**, klicken Sie auf **Umbenennen**, und geben Sie anschließend einen Namen für den Regelsatzordner ein.  
  
#### So erstellen Sie den Eincheckrichtlinien\-Regelsatz  
  
1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie auf **Datei**.  
  
2.  Klicken Sie in der Liste **Kategorien** auf **Allgemein**.  
  
3.  Doppelklicken Sie in der Liste **Vorlagen** auf **Regelsatz für Codeanalyse**.  
  
4.  Geben Sie die gewünschten Regeln für den Regelsatz an, und speichern Sie die Regelsatzdatei im zuvor erstellten Regelsatzordner.  
  
     Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### So fügen Sie die Regelsatzdatei der Versionskontrolle hinzu  
  
1.  Klicken Sie im Quellcodeverwaltungs\-Explorer mit der rechten Maustaste auf den neuen Ordner, und klicken Sie anschließend auf **Elemente zu Ordner hinzufügen**.  
  
     Weitere Informationen finden Sie unter [Verwenden der Versionskontrolle](../Topic/Use%20version%20control.md).  
  
2.  Klicken Sie auf die erstellte Regelsatzdatei und anschließend auf **Fertig stellen**.  
  
     Die Datei wird der Quellcodeverwaltung hinzugefügt und für Sie ausgecheckt.  
  
3.  Klicken Sie im Detailfenster des Quellcodeverwaltungs\-Explorers mit der rechten Maustaste auf den Dateinamen, und klicken Sie anschließend auf **Ausstehende Änderungen einchecken**.  
  
4.  Im Dialogfeld **Einchecken** können Sie ggf. einen Kommentar hinzufügen. Klicken Sie anschließend auf **Einchecken**.  
  
    > [!NOTE]
    >  Wenn Sie bereits eine Codeanalyse\-Eincheckrichtlinie für das Teamprojekt konfiguriert haben und das Kontrollkästchen **Einchecken von Dateien erzwingen, sodass nur Dateien enthalten sind, die Teil der aktuellen Projektmappe sind** aktiviert ist, wird eine Richtlinienfehlerwarnung ausgelöst.  Aktivieren Sie im Dialogfeld "Richtlinienfehler" das Kontrollkästchen **Richtlinienfehler überschreiben und Eincheckvorgang fortsetzen**.  Fügen Sie einen erforderlichen Kommentar hinzu, und klicken Sie anschließend auf **OK**.  
  
#### So geben Sie die Regelsatzdatei als Eincheckrichtlinie an  
  
1.  Zeigen Sie im Menü **Team** auf **Teamprojekteinstellungen**, und klicken Sie anschließend auf **Quellcodeverwaltung**.  
  
2.  Klicken Sie auf **Eincheckrichtlinie** und anschließend auf **Hinzufügen**.  
  
3.  Doppelklicken Sie in der Liste **Eincheckrichtlinien** auf **Codeanalyse**, und vergewissern Sie sich, dass das Kontrollkästchen **Codeanalyse für verwalteten Code erzwingen** aktiviert ist.  
  
4.  In der Liste **Diesen Regelsatz ausführen**  klicken Sie auf **\<Regelsatz aus Quellcodeverwaltung auswählen\>**.  
  
5.  Geben Sie den Pfad der Regelsatzdatei für die Eincheckrichtlinie in der Versionskontrolle ein.  
  
     Der Pfad muss der folgenden Syntax entsprechen:  
  
     **$\/** `TeamProjectName` **\/** `VersionControlPath`  
  
    > [!NOTE]
    >  Sie können den Pfad mithilfe einer der folgenden Prozeduren im Quellcodeverwaltungs\-Explorer kopieren:  
  
    -   Klicken Sie im Bereich **Ordner** auf den Ordner, der die Regelsatzdatei enthält.  Kopieren Sie den Versionskontrollpfad des Ordners, der im Feld **Quelle** angezeigt wird, und geben Sie den Namen der Regelsatzdatei manuell ein.  
  
    -   Klicken Sie im Detailfenster mit der rechten Maustaste auf die Regelsatzdatei, und klicken Sie anschließend auf **Eigenschaften**.  Kopieren Sie auf der Registerkarte **Allgemein** den Wert unter **Servername**.  
  
## Synchronisieren von Codeprojekten mit dem Eincheckrichtlinien\-Regelsatz  
 Ein Eincheckrichtlinien\-Regelsatz für ein Teamprojekt wird im Eigenschaftendialogfeld des Codeprojekts als Codeanalyseregelsatz einer Codeprojektkonfiguration angegeben.  Befindet sich der Regelsatz auf dem gleichen Laufwerk wie das Codeprojekt, wird der Regelsatz mithilfe eines relativen Pfads angegeben, wenn der Pfad im Dateidialogfeld ausgewählt wird.  Dank des relativen Pfads sind die Einstellungen der Projekteigenschaften auf andere Computer übertragbar, sofern auf diesen ähnliche lokale Versionskontrollstrukturen vorhanden sind.  
  
#### So geben Sie einen Teamprojekt\-Regelsatz als Regelsatz eines Codeprojekts an  
  
1.  Rufen Sie ggf. den Regelsatzordner und die Regelsatzdatei der Eincheckrichtlinie aus der Versionskontrolle ab.  
  
     Klicken Sie hierzu im Quellcodeverwaltungs\-Explorer mit der rechten Maustaste auf den Regelsatzordner, und klicken Sie anschließend auf **Letzte Version abrufen**.  
  
2.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf das Codeprojekt, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie auf **Codeanalyse**.  
  
4.  Klicken Sie ggf. in den Listen **Konfiguration** und **Plattform** auf die entsprechenden Optionen.  
  
5.  Aktivieren Sie das Kontrollkästchen **Codeanalyse beim Erstellen aktivieren \(definiert die CODE\_ANALYSIS\-Konstante\)**, damit die Codeanalyse bei jeder Erstellung des Projekts mit der angegebenen Konfiguration ausgeführt wird.  
  
6.  Aktivieren Sie das Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken**, um Code in Komponenten anderer Unternehmen zu ignorieren.  
  
7.  In der Liste **Diesen Regelsatz ausführen**  klicken Sie auf **\<Durchsuchen...\>**.  
  
8.  Geben Sie die lokale Version der Eincheckrichtlinien\-Regelsatzdatei an.