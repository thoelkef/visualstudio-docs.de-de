---
title: 'Exemplarische Vorgehensweise: Analysieren von C/C++-Code für Mängel | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 3c4c0a053a103ec719792acd7b5d234aa99154ac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Exemplarische Vorgehensweise: Analysieren von C/C++-Code auf Fehler

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie C/C++-Code für potenzielle Codefehler zu analysieren, indem Sie das Codeanalysetool für C/C++-Code. 

- Ausführen der Codeanalyse für systemeigenen Code.
- Analysieren von Code (Warnungen) austragen.
- Treat Warnung als Fehler.
- Kommentieren Sie Quellcode um defekt Codeanalyse zu verbessern.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Eine Kopie der [Demobeispiel](../code-quality/demo-sample.md).
- Grundlegendes Verständnis von C/C++.

### <a name="to-run-code-defect-analysis-on-native-code"></a>Zum Ausführen von defekt Codeanalyse auf systemeigenen code

1. Öffnen Sie die Projektmappe Demo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     Die Demo-Projektmappe jetzt füllt **Projektmappen-Explorer**.

2. Auf der **erstellen** Menü klicken Sie auf **Projektmappe neu erstellen**.

     Die Projektmappe ohne Fehler oder Warnungen erstellt wird.

3. In **Projektmappen-Explorer**, wählen Sie das Projekt CodeDefects.

4. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Die **CodeDefects-Eigenschaftenseiten** Dialogfeld wird angezeigt.

5. Klicken Sie auf **Codeanalyse**.

6. Klicken Sie auf die **Codeanalyse für C/C++ auf Build aktivieren** Kontrollkästchen.

7. Erstellen Sie das Projekt CodeDefects neu.

     Codeanalysewarnungen werden angezeigt, der **Fehlerliste**.

### <a name="to-analyze-code-defect-warnings"></a>Analysieren Sie Fehler in Code (Warnungen)

1. Auf der **Ansicht** Menü klicken Sie auf **Fehlerliste**.

     Abhängig vom Entwicklerprofil, die im ausgewählten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Ihnen zu zeigen **Weitere Fenster** auf die **Ansicht** Menü, und klicken Sie dann auf **Fehlerliste**.

2. In der **Fehlerliste**, doppelklicken Sie auf die folgende Warnung:

     Warnung C6230: implizite Umwandlung zwischen semantisch unterschiedlichen Typen: Verwenden von HRESULT in ein Boolean-Kontext.

     Der Code-Editor zeigt die Zeile, die die Warnung verursacht, in der Funktion hat `bool``ProcessDomain()`. Diese Warnung gibt an, dass ein HRESULT in einer 'if'-Anweisung verwendet wird, obwohl ein boolesches Ergebnis erwartet wird.

3. Beheben Sie diese Warnung wird unter Verwendung des Makros SUCCEEDED. Der Code sollte dem folgenden Code ähneln:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. In der **Fehlerliste**, doppelklicken Sie auf die folgende Warnung:

     Warnung C6282: Falscher Operator: Zuweisung zu Konstante im Testkontext. War == beabsichtigt?

5. Diese Warnung zu korrigieren, Testen auf Gleichheit. Der Code sollte ähnlich dem folgenden Code aussehen:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Warnung als Fehler behandelt.

1. Fügen Sie in der Datei Bug.cpp Folgendes `#pragma` Anweisung am Anfang der Datei, die die Warnung C6001 als Fehler zu behandeln:

   ```cpp
   #pragma warning (error: 6001)
   ```

2. Erstellen Sie das Projekt CodeDefects neu.

     In der **Fehlerliste**, C6001 jetzt als Fehler angezeigt wird.

3. Beheben Sie die verbleibenden beiden C6001-Fehler in der **Fehlerliste** durch initialisieren `i` und `j` auf 0.

4. Erstellen Sie das Projekt CodeDefects neu.

     Das Projekt erstellt, ohne alle Warnungen oder Fehler.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>So beheben Sie die Source Code Annotation-Warnungen in annotation.c

1. Wählen Sie im Projektmappen-Explorer das Projekt Anmerkungen.

2. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Die **Anmerkungen Eigenschaftenseiten** Dialogfeld wird angezeigt.

3. Klicken Sie auf **Codeanalyse**.

4. Wählen Sie die **Codeanalyse für C/C++ auf Build aktivieren** Kontrollkästchen.

5. Das Annotations-Projekt neu.

6. In der **Fehlerliste**, doppelklicken Sie auf die folgende Warnung:

     Warnung C6011: NULL-Zeiger 'NewNode' Dereferenzierung.

     Diese Warnung gibt an, vom Aufrufer Fehler, um den Rückgabewert zu überprüfen. In diesem Fall ein Aufruf von **AllocateNode** kann einen NULL-Wert zurückzugeben (siehe die annotations.h-Headerdatei für die Funktionsdeklaration AllocateNode).

7. Öffnen Sie die Datei annotations.cpp.

8. Um diese Warnung zu beheben, verwenden Sie eine 'if'-Anweisung so testen Sie den Rückgabewert aus. Der Code sollte dem folgenden Code ähneln:

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. Das Annotations-Projekt neu.

     Das Projekt erstellt, ohne alle Warnungen oder Fehler.

### <a name="to-use-source-code-annotation"></a>Source Code Annotation verwenden

1. Kommentieren Sie formale Parameter und Rückgabewert der Funktion `AddTail` Pre- und Post-Bedingungen mit, wie im folgenden Beispiel gezeigt:

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. Erstellen Sie Annotations-Projekt neu.

3. In der **Fehlerliste**, doppelklicken Sie auf die folgende Warnung:

     Warnung C6011: NULL-Zeiger "Knoten".

     Diese Warnung gibt an, dass der Knoten, die an die Funktion übergeben null sein kann, und gibt die Zeilennummer, in dem die Warnung ausgelöst wurde.

4. Um diese Warnung zu beheben, verwenden Sie eine 'if'-Anweisung so testen Sie den Rückgabewert aus. Der Code sollte dem folgenden Code ähneln:

   ```cpp
   . . .
   LinkedList *newNode = NULL; 
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. Erstellen Sie Annotations-Projekt neu.

     Das Projekt erstellt, ohne alle Warnungen oder Fehler.

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweise: Analysieren von verwaltetem Code Codefehler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[für C/C++-Codeanalyse](../code-quality/code-analysis-for-c-cpp-overview.md)