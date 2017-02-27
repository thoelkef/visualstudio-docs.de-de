---
title: "Arbeiten mit dem Regelsatz-Editor f&#252;r die Codeanalyse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.ruleseteditor"
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Arbeiten mit dem Regelsatz-Editor f&#252;r die Codeanalyse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Regelsatz\-Editor für die Codeanalyse ermöglicht es Ihnen, die Regeln in einem benutzerdefinierten Regelsatz und die Aktion anzugeben.  Sie können auch die Aktion angeben, die ausgeführt werden soll, wenn die Codeanalyse einen Verstoß gegen die Regel feststellt.  
  
|Aktion|**Beschreibung**|  
|------------|----------------------|  
|**Warning**|Generiert eine Warnung im Fenster **Fehlerliste**.|  
|**Error**|Generiert einen Fehler im Fenster **Fehlerliste**.|  
|**None**|Deaktiviert die Regel.|  
  
 Der Editor zeigt die Regeln in einer Struktur an, in der die Regeln nach dem von Ihnen angegebenen Regelsatzfeld gruppiert werden.  Führen Sie einen oder mehrere der folgenden Schritte aus, um Regeln einem Regelsatz hinzuzufügen oder daraus zu entfernen:  
  
-   Aktivieren oder deaktivieren Sie das Kontrollkästchen des Gruppenknotens, um alle Regeln der Gruppe hinzuzufügen oder zu entfernen.  Wenn Sie eine Gruppe auswählen, wird für alle Regeln die Warnaktion festgelegt.  
  
-   Klicken Sie auf das Feld **Aktion** einer Gruppe, und geben Sie dann die Aktion an, die für alle Regeln in der Gruppe gelten soll.  
  
-   Aktivieren oder deaktivieren Sie das Kontrollkästchen einer einzelnen Regel.  Wenn Sie das Kontrollkästchen für eine Regel aktivieren, wird die Regel auf die Warnaktion festgelegt.  
  
## Symbolleiste des Regelsatz\-Editors  
 Mit der Symbolleiste des Regelsatz\-Editors können Sie die Daten, die im Regelsatzraster angezeigt werden, gruppieren, filtern und durchsuchen.  
  
 In der folgenden Tabelle werden die Steuerelemente der Symbolleiste des Regelsatz\-Editors beschrieben.  
  
|Steuerelement der Symbolleiste|**Beschreibung**|  
|------------------------------------|----------------------|  
|**Alle erweitern**|Zeigt die Regeln in allen Gruppen an.|  
|**Alle reduzieren**|Blendet die Regeln in allen Gruppen aus.|  
|**Group By**|Gibt das Feld an, nach dem Regeln gruppiert werden.  Klicken auf **\<Keine\>**, um die Regeln ohne Gruppen anzuzeigen.|  
|**Spaltenoptionen**|Gibt die Regelfelder an, die angezeigt werden sollen.|  
|**Regeln ausblenden, die auf die aktuelle Projektmappe nicht zutreffen**|Zeigt Regeln an, die nicht dem gleichen Zieltyp wie die Projektmappe entsprechen, oder blendet diese aus.|  
|**Regeln anzeigen, die Codeanalysefehler generieren können**|Zeigt Regeln an, denen die Fehleraktion zugewiesen wurde, oder blendet diese aus.|  
|**Regeln anzeigen, die Codeanalysewarnungen generieren können**|Zeigt Regeln an, denen die Warnaktion zugewiesen wurde, oder blendet diese aus.|  
|**Nicht aktivierte Regeln anzeigen**|Zeigt Regeln an, denen die Aktion "Keine" zugewiesen wurde, oder blendet diese aus.|  
|**Untergeordnete Regelsätze hinzufügen oder entfernen**|Fügt die Regeln den ausgewählten Regelsätzen hinzu oder entfernt sie.|  
|**Suchregeln**|Sucht in allen Feldwerten nach der Zeichenfolge, die Sie angeben.|  
  
## Regelsatzfelder  
 Regelsatzfelder zeigen Informationen zu einem Regelsatz an und können zum Sortieren und Gruppieren der Regelliste verwendet werden.  Um Felder ein\- oder auszublenden, klicken Sie auf der Symbolleiste des Regelsatz\-Editors auf **Spaltenoptionen**, und aktivieren oder deaktivieren Sie die Kontrollkästchen der Felder, die ein\- oder ausgeblendet werden sollen.  
  
 In der folgenden Tabelle werden die Felder eines Regelsatzes beschrieben.  
  
|Feld|**Beschreibung**|  
|----------|----------------------|  
|**ID**|Der Bezeichner der Regel.|  
|**Category**|Zusätzlich zu ihrer Zugehörigkeit zu Regelsätzen werden Codeanalyseregeln auch nach Kategorien gruppiert.  Weitere Informationen finden Sie unter [Warnungen bei der Analyse von verwaltetem Code](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Name**|Der Titel der Regel.|  
|**Namespace**|Der Namespace der Regel.|  
|**Target Type**|Gibt an, ob die Regel für systemeigenen, verwalteten oder Datenbankcode gilt.|  
|**Action**|Die Aktion, die bei einem Verstoß gegen die Regel während einer Codeanalyseausführung ausgeführt wird.<br /><br /> **Warning** – erzeugt eine Warnung.<br /><br /> **Error**\- erzeugt einen Fehler.<br /><br /> **None** \- deaktiviert die Regel.<br /><br /> Sie können das Aktionsfeld bearbeiten.  Wenn der Wert auf \<Keine\> festgelegt ist, hat das die gleichen Auswirkungen wie eine Deaktivierung des Kontrollkästchens für die Regel.|  
|**Source Rule Sets**|Der Regelsatz, der die Regel enthält.|  
  
## Sortieren und Filtern von Regelsätzen  
 Über die Spaltenüberschriften des Regelsatzrasters können Sie die Regeln nach den Werten des Felds sortieren und filtern.  
  
-   Klicken Sie zum Sortieren der Regelsatzlisten auf die Spaltenüberschrift des Felds, nach dem sortiert werden soll.  Wenn die Regelsätze gruppiert werden, wird jede Gruppe einzeln sortiert.  
  
-   Klicken Sie zum Filtern der Regelsätze nach dem Wert eines Felds auf die Filterschaltfläche der Spaltenüberschrift des Felds, nach dem Sie filtern möchten.  Aktivieren Sie die Kontrollkästchen der Werte, die angezeigt werden sollen, und deaktivieren Sie die Werte der Kontrollkästchen, die ausgeblendet werden sollen.