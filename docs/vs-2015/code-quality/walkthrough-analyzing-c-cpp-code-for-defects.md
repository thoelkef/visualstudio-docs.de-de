---
title: 'Exemplarische Vorgehensweise: Analysieren von C / C++-Code auf Fehler | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: dcd862b6ff9c94b8de3fc8b5a56164549fefe8ca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142029"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Exemplarische Vorgehensweise: Analysieren von C/C++-Code im Hinblick auf Fehler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird das C/C++-Code für potenzielle Fehler zu analysieren, indem Sie mit dem Code Analysis-Tool für C/C++-Code veranschaulicht.  
  
 In dieser exemplarischen Vorgehensweise Schritt für Schritt durch den Prozess mit der Codeanalyse von C/C++-Code potenzielle Fehler zu analysieren.  
  
 Sie führen die folgenden Schritte aus:  
  
- Codeanalyse für systemeigenen Code ausführen.  
  
- Analysieren Sie Fehler für Code (Warnungen).  
  
- Behandeln Sie Warnung als Fehler.  
  
- Kommentieren Sie Quellcode, um Fehler der Codeanalyse zu verbessern.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] oder [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].  
  
- Eine Kopie der [Demobeispiel](../code-quality/demo-sample.md).  
  
- Grundlegende Kenntnisse von C/C++.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Fehler der Codeanalyse auf systemeigenen Code ausführen  
  
1. Öffnen Sie die Demo-Projektmappe in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Die Demoprojektmappe jetzt wird **Projektmappen-Explorer**.  
  
2. Klicken Sie im Menü **Build** auf **Projektmappe neu erstellen**.  
  
     Die Projektmappe ohne Fehler oder Warnungen wird erstellt.  
  
3. In **Projektmappen-Explorer**, wählen Sie das Projekt CodeDefects.  
  
4. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
     Die **CodeDefects Eigenschaftenseiten** Dialogfeld wird angezeigt.  
  
5. Klicken Sie auf **Codeanalyse**.  
  
6. Klicken Sie auf die **Codeanalyse für C/C++ auf Build aktivieren** Kontrollkästchen.  
  
7. Erstellen Sie das Projekt CodeDefects neu.  
  
     Codeanalysewarnungen werden angezeigt, der **Fehlerliste**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Analysieren von Code (Warnungen) der Mängel  
  
1. Klicken Sie im Menü **Ansicht** auf **Fehlerliste**.  
  
     Abhängig von der Developer-Profil, das in ausgewählten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], möglicherweise müssen Sie es auf **Other Windows** auf die **Ansicht** , und klicken Sie dann auf **Fehlerliste**.  
  
2. In der **Fehlerliste**, doppelklicken Sie auf die folgende Warnung:  
  
     Warnung C6230: Implizite Umwandlung zwischen semantisch unterschiedlichen Typen: HRESULT in einen Boolean-Kontext verwenden.  
  
     Der Code-Editor zeigt die Codezeile, die die Warnung verursacht, in der Funktion hat `bool``ProcessDomain()`. Diese Warnung gibt an, dass ein HRESULT in einen "if"-Anweisung verwendet wird, wo ein boolesches Ergebnis erwartet wird.  
  
3. Korrigieren Sie diese Warnung mit dem SUCCEEDED-Makro. Ihr Code sollte dem folgenden Code ähneln:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4. In der **Fehlerliste**, doppelklicken Sie auf die folgende Warnung:  
  
     Warnung C6282: Falscher Operator: Zuweisung zu Konstante im Testkontext. War == beabsichtigt?  
  
5. Korrigieren Sie diese Warnung, indem Sie auf Gleichheit. Der Code sollte ähnlich dem folgenden Code aussehen:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Warnung als Fehler behandelt.  
  
1. Fügen Sie die folgenden, in der Datei Bug.cpp `#pragma` Anweisung am Anfang der Datei, die die Warnung C6001 als Fehler behandeln:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2. Erstellen Sie das Projekt CodeDefects neu.  
  
     In der **Fehlerliste**, C6001 wird jetzt als Fehler.  
  
3. Korrigieren Sie die verbleibenden zwei C6001 Fehler in der **Fehlerliste** initialisieren `i` und `j` auf 0.  
  
4. Erstellen Sie das Projekt CodeDefects neu.  
  
     Das Projekt erstellt, ohne alle Warnungen oder Fehler.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Um die Source Code Annotation-Warnungen in annotation.c zu beheben.  
  
1. Wählen Sie im Projektmappen-Explorer das Annotations-Projekt ein.  
  
2. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
     Die **Annotations-Eigenschaftenseiten** Dialogfeld wird angezeigt.  
  
3. Klicken Sie auf **Codeanalyse**.  
  
4. Wählen Sie die **Codeanalyse für C/C++ auf Build aktivieren** Kontrollkästchen.  
  
5. Erstellen Sie das Annotations-Projekt neu.  
  
6. In der **Fehlerliste**, doppelklicken Sie auf die folgende Warnung:  
  
     Warnung C6011: Dereferenzierender NULL-Zeiger "NewNode".  
  
     Diese Warnung gibt an, dass der Aufrufer den Rückgabewert zu überprüfen. In diesem Fall ein Aufruf von **AllocateNode** möglicherweise einen NULL-Wert zurück (siehe die annotations.h-Headerdatei für die Funktionsdeklaration für AllocateNode).  
  
7. Öffnen Sie die Datei annotations.cpp.  
  
8. Um diese Warnung zu korrigieren, verwenden Sie eine "if"-Anweisung, um den Rückgabewert zu testen. Ihr Code sollte dem folgenden Code ähneln:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Erstellen Sie das Annotations-Projekt neu.  
  
     Das Projekt erstellt, ohne alle Warnungen oder Fehler.  
  
### <a name="to-use-source-code-annotation"></a>Verwenden von Code quellcodeanmerkungen  
  
1. Kommentieren Sie die formalen Parameter und Rückgabewert der Funktion `AddTail` mithilfe der Pre- und Post-Bedingungen, wie im folgenden Beispiel gezeigt:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2. Erstellen Sie Annotations-Projekt neu.  
  
3. In der **Fehlerliste**, doppelklicken Sie auf die folgende Warnung:  
  
     Warnung C6011: Dereferenzierender NULL-Zeiger "Node".  
  
     Diese Warnung gibt an, dass der Knoten, die an die Funktion übergeben möglicherweise null ist, und gibt die Nummer der Zeile, in dem die Warnung ausgelöst wurde.  
  
4. Um diese Warnung zu korrigieren, verwenden Sie eine "if"-Anweisung, um den Rückgabewert zu testen. Ihr Code sollte dem folgenden Code ähneln:  
  
    ```  
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
 [Exemplarische Vorgehensweise: Analysieren von verwaltetem Code im Hinblick auf Codefehler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
