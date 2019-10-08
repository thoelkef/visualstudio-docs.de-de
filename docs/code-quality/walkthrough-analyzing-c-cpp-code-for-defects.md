---
title: 'Exemplarische Vorgehensweise: Analysieren von C/C++-Code im Hinblick auf Fehler'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: bdb99cf487995859b9623f11b3559f1b5e7e3ca7
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018340"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Exemplarische Vorgehensweise: Analysieren von C/C++-Code im Hinblick auf Fehler

In dieser exemplarischen Vorgehensweise wird veranschaulicht,C++ wie c/Code mit dem Code Analysetool für C/C++ Code auf potenzielle Code Fehler analysiert wird.

- Ausführen der Code Analyse für nativen Code.
- Analysieren von Code Fehler Warnungen.
- Behandeln Sie die Warnung als Fehler.
- Kommentieren Sie den Quellcode, um die Code Fehleranalyse zu verbessern.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Eine Kopie des [Demo](../code-quality/demo-sample.md)Beispiels.
- Grundlegendes Verständnis von CC++/.

### <a name="to-run-code-defect-analysis-on-native-code"></a>So führen Sie die Code Fehleranalyse für nativen Code aus

1. Öffnen Sie die Demo Projekt Mappe in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     Die Demo Lösung füllt nun **Projektmappen-Explorer**auf.

2. Klicken Sie im Menü **Build** auf **Projektmappe neu erstellen**.

     Die Lösung wird ohne Fehler oder Warnungen erstellt.

3. Wählen Sie in **Projektmappen-Explorer**das Projekt codemängel aus.

4. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Das Dialogfeld **Codedefekte-Eigenschaften Seiten** wird angezeigt.

5. Klicken Sie auf **Code Analyse**.

6. Aktivieren Sie das Kontrollkästchen **Code Analyse fürC++ C/on-Build aktivieren** .

7. Erstellen Sie das Projekt "codemängel" neu.

     Code Analyse Warnungen werden in der **Fehlerliste**angezeigt.

### <a name="to-analyze-code-defect-warnings"></a>So analysieren Sie Code Fehler Warnungen

1. Klicken Sie im Menü **Ansicht** auf **Fehlerliste**.

     Abhängig vom Entwickler Profil, das Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgewählt haben, müssen Sie möglicherweise im Menü **Ansicht** auf **andere Fenster** zeigen und dann auf **Fehlerliste**klicken.

2. Doppelklicken Sie im **Fehlerliste**auf die folgende Warnung:

     Warnung C6230: Implizite Umwandlung zwischen semantisch unterschiedlichen Typen: HRESULT wird in einem Boolean-Kontext verwendet.

     Der Code-Editor zeigt die Zeile, die die Warnung verursacht hat, in der-Funktion an `bool ProcessDomain()`. Diese Warnung gibt an, dass ein HRESULT in einer if-Anweisung verwendet wird, in der ein boolesches Ergebnis erwartet wird.

3. Korrigieren Sie diese Warnung, indem Sie das Makro "erfolgreich" verwenden. Der Code sollte dem folgenden Code ähneln:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. Doppelklicken Sie im **Fehlerliste**auf die folgende Warnung:

     Warnung C6282: Falscher Operator: Zuweisung zu konstanter im Test Kontext. Was = = beabsichtigt?

5. Korrigieren Sie diese Warnung, indem Sie auf Gleichheit testen. Der Code sollte in etwa wie der folgende Code aussehen:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>So behandeln Sie die Warnung als Fehler

1. Fügen Sie in der Datei Bug. cpp am Anfang der Datei die folgende `#pragma`-Anweisung hinzu, um die Warnung C6001 als Fehler zu behandeln:

   ```cpp
   #pragma warning (error: 6001)
   ```

2. Erstellen Sie das Projekt "codemängel" neu.

     Im **Fehlerliste**wird C6001 jetzt als Fehler angezeigt.

3. Korrigieren Sie die verbleibenden zwei C6001-Fehler im **Fehlerliste** , indem Sie `i` und `j` auf 0 initialisieren.

4. Erstellen Sie das Projekt "codemängel" neu.

     Das Projekt wird ohne Warnungen oder Fehler erstellt.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>So korrigieren Sie die Warnungen der Quell Code Anmerkung in der Anmerkung. c

1. Wählen Sie in Projektmappen-Explorer das Projekt Annotations aus.

2. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Das Dialogfeld **Annotations-Eigenschaften Seiten** wird angezeigt.

3. Klicken Sie auf **Code Analyse**.

4. Aktivieren Sie das Kontrollkästchen **Code Analyse fürC++ C/on-Build aktivieren** .

5. Erstellen Sie das Projekt Annotations neu.

6. Doppelklicken Sie im **Fehlerliste**auf die folgende Warnung:

     Warnung C6011: Dereferenzierender NULL-Zeiger "newNode".

     Diese Warnung weist darauf hin, dass der Aufrufer den Rückgabewert nicht überprüfen konnte. In diesem Fall kann ein Rückruf von " **Zuordnungs-Ode** " einen NULL-Wert zurückgeben (Weitere Informationen finden Sie in der Annotations. h-Header Datei für die Funktionsdeklaration für "zustellerode")

7. Öffnen Sie die Datei "Annotations. cpp".

8. Um diese Warnung zu korrigieren, verwenden Sie eine if-Anweisung, um den Rückgabewert zu testen. Der Code sollte dem folgenden Code ähneln:

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. Erstellen Sie das Projekt Annotations neu.

     Das Projekt wird ohne Warnungen oder Fehler erstellt.

### <a name="to-use-source-code-annotation"></a>So verwenden Sie die Quell Code Anmerkung

1. Kommentieren Sie formale Parameter und den Rückgabewert der Funktion `AddTail`, indem Sie die Pre-und Post-Bedingungen wie im folgenden Beispiel gezeigt verwenden:

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. Projekt zum erneuten Erstellen von Anmerkungen.

3. Doppelklicken Sie im **Fehlerliste**auf die folgende Warnung:

     Warnung C6011: Dereferenzierender NULL-Zeiger "Node".

     Diese Warnung gibt an, dass der an die Funktion eingegebene Knoten NULL sein kann, und gibt die Nummer der Zeile an, in der die Warnung ausgelöst wurde.

4. Um diese Warnung zu korrigieren, verwenden Sie eine if-Anweisung, um den Rückgabewert zu testen. Der Code sollte dem folgenden Code ähneln:

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. Projekt zum erneuten Erstellen von Anmerkungen.

     Das Projekt wird ohne Warnungen oder Fehler erstellt.

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweise: Analysieren von verwaltetem Code auf Code Fehler @ no__t-0 @ no__t-1[Code Analyse fürC++ C/](../code-quality/code-analysis-for-c-cpp-overview.md)
