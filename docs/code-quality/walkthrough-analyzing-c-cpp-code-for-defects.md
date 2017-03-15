---
title: "Exemplarische Vorgehensweise: Analysieren von C/C++-Code auf Fehler | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "C/C++, Codeanalyse"
  - "Codeanalysetool, Exemplarische Vorgehensweisen"
  - "Codeanalyse, Exemplarische Vorgehensweisen"
  - "Code, Analysieren von C/C++"
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 35
caps.handback.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Analysieren von C/C++-Code auf Fehler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise veranschaulicht, wie C\/C\+\+\-Code mithilfe des Codeanalysetools für C\/C\+\+\-Code auf potenzielle Fehler analysiert wird.  
  
 Im Folgenden wird exemplarisch Schritt für Schritt die Verwendung der Codeanalyse zum Auffinden potenzieller Fehler im C\/C\+\+\-Code beschrieben.  
  
 Sie führen dabei folgende Schritte aus:  
  
-   Ausführen der Codeanalyse für systemeigenen Code  
  
-   Analysieren von Codefehlerwarnungen  
  
-   Behandeln von Warnungen als Fehler  
  
-   Hinzufügen von Anmerkungen zum Quellcode zur Verbesserung der Codefehleranalyse  
  
## Vorbereitungsmaßnahmen  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] oder [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].  
  
-   Eine Kopie von [Demobeispiel](../code-quality/demo-sample.md).  
  
-   Ein grundlegendes Verständnis von C\/C\+\+  
  
### So führen Sie die Codefehleranalyse für systemeigenem Code aus  
  
1.  Öffnen Sie die Demoprojektmappe in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Die Demoprojektmappe wird jetzt im **Projektmappen\-Explorer** angezeigt.  
  
2.  Klicken Sie im Menü **Erstellen** auf **Projektmappe neu erstellen**.  
  
     Die Projektmappe wird ohne Fehler oder Warnungen erstellt.  
  
3.  Wählen Sie im **Projektmappen\-Explorer** das Projekt CodeDefects aus.  
  
4.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
     Das Dialogfeld **CodeDefects\-Eigenschaftenseiten** wird angezeigt.  
  
5.  Klicken Sie auf **Codeanalyse**.  
  
6.  Klicken Sie auf das Kontrollkästchen **Codeanalyse für C\/C\+\+ beim Erstellen aktivieren**.  
  
7.  Erstellen Sie das Projekt CodeDefects neu.  
  
     In der **Fehlerliste** werden Codeanalysewarnungen angezeigt.  
  
### So analysieren Sie Codefehlerwarnungen  
  
1.  Klicken Sie im Menü **Ansicht** auf **Fehlerliste**.  
  
     Abhängig vom Entwicklerprofil, das in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgewählt wurde, müssen Sie im Menü **Ansicht** möglicherweise zuerst auf **Weitere Fenster** zeigen, bevor Sie auf **Fehlerliste** klicken können.  
  
2.  Doppelklicken Sie in der **Fehlerliste** auf die folgende Warnung:  
  
     Warnung C6230: Implizite Umwandlung zwischen semantisch unterschiedlichen Integer\-Typen: HRESULT wird in einem Boolean\-Kontext verwendet.  
  
     Die Zeile, die die Warnung in der Funktion `bool` `ProcessDomain()` verursacht hat, wird im Code\-Editor angezeigt.  Diese Warnung bedeutet, dass in einer 'if'\-Anweisung HRESULT verwendet wird, obwohl ein boolesches Ergebnis erwartet wurde.  
  
3.  Korrigieren Sie diese Warnung mithilfe des SUCCEEDED\-Makros.  Der Code sollte in etwa dem folgenden Beispiel entsprechen:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4.  Doppelklicken Sie in der **Fehlerliste** auf die folgende Warnung:  
  
     Warnung C6282: Falscher Operator: Zuweisung zu Konstante in Testkontext.  War \=\= beabsichtigt?  
  
5.  Korrigieren Sie diese Warnung, indem Sie auf Gleichheit testen.  Der Code sollte ungefähr wie folgt aussehen:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### So behandeln Sie Warnungen als Fehler  
  
1.  Fügen Sie am Anfang der Datei Bug.cpp die folgende `#pragma`\-Anweisung hinzu, um die Warnung C6001 als Fehler zu behandeln:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2.  Erstellen Sie das Projekt CodeDefects neu.  
  
     In der **Fehlerliste** wird C6001 jetzt als Fehler angezeigt.  
  
3.  Korrigieren Sie die verbleibenden beiden C6001\-Fehler in der **Fehlerliste**, indem Sie `i` und `j` mit 0 \(null\) initialisieren.  
  
4.  Erstellen Sie das Projekt CodeDefects neu.  
  
     Das Projekt wird ohne Warnungen oder Fehler erstellt.  
  
### So korrigieren Sie die Warnungen zu Quellcodeanmerkungen in annotation.c  
  
1.  Wählen Sie im Projektmappen\-Explorer das Projekt Annotations aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
     Das Dialogfeld **Annotations\-Eigenschaftenseiten** wird angezeigt.  
  
3.  Klicken Sie auf **Codeanalyse**.  
  
4.  Aktivieren Sie das Kontrollkästchen **Codeanalyse für C\/C\+\+ beim Erstellen aktivieren**.  
  
5.  Erstellen Sie das Projekt Annotations neu.  
  
6.  Doppelklicken Sie in der **Fehlerliste** auf die folgende Warnung:  
  
     Warnung C6011: NULL\-Zeiger 'newNode' wird dereferenziert.  
  
     Diese Warnung gibt an, dass der Aufrufer den Rückgabewert nicht überprüfen kann.  In diesem Fall wird bei einem Aufruf von **AllocateNode** möglicherweise ein NULL\-Wert zurückgegeben. \(Die Funktionsdeklaration für AllocateNode finden Sie in der Headerdatei annotations.h\).  
  
7.  Öffnen Sie die Datei "annotations.cpp".  
  
8.  Verwenden Sie zum Korrigieren dieser Warnung eine 'if'\-Anweisung, um den Rückgabewert zu testen.  Der Code sollte in etwa dem folgenden Beispiel entsprechen:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Erstellen Sie das Projekt Annotations neu.  
  
     Das Projekt wird ohne Warnungen oder Fehler erstellt.  
  
### So verwenden Sie Quellcodeanmerkungen  
  
1.  Fügen Sie den formalen Parametern und dem Rückgabewert der Funktion `AddTail` mithilfe der Vor\- und Nachbedingung Anmerkungen hinzu, wie in diesem Beispiel dargestellt:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2.  Erstellen Sie das Projekt Annotations neu.  
  
3.  Doppelklicken Sie in der **Fehlerliste** auf die folgende Warnung:  
  
     Warnung C6011: NULL\-Zeiger 'node' wird dereferenziert.  
  
     Mit dieser Warnung wird angegeben, dass der an die Funktion übergebene Knoten möglicherweise NULL ist. Darüber hinaus ist die Nummer der Zeile angegeben, in der die Warnung ausgelöst wurde.  
  
4.  Verwenden Sie zum Korrigieren dieser Warnung eine 'if'\-Anweisung, um den Rückgabewert zu testen.  Der Code sollte in etwa dem folgenden Beispiel entsprechen:  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5.  Erstellen Sie das Projekt Annotations neu.  
  
     Das Projekt wird ohne Warnungen oder Fehler erstellt.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Analysieren von verwaltetem Code auf Codefehler](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)