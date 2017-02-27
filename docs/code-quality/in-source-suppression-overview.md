---
title: "&#220;bersicht &#252;ber die Unterdr&#252;ckung im Quellcode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Quellenunterdrückung, Codeanalyse"
  - "Codeanalyse, Quellenunterdrückung"
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 40
---
# &#220;bersicht &#252;ber die Unterdr&#252;ckung im Quellcode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bei der Unterdrückung im Quellcode handelt es sich um die Möglichkeit, Verletzungen der Codeanalyseregeln in verwaltetem Code zu unterdrücken, indem das **SuppressMessage**\-Attribut den Codesegmenten hinzugefügt wird, die die Verletzungen verursacht haben.  Das bedingte **SuppressMessage**\-Attribut wird nur dann in die IL\-Metadaten einer Assembly mit verwaltetem Code eingeschlossen, wenn das CODE\_ANALYSIS\-Kompilierungssymbol zur Kompilierungszeit definiert wird.  
  
 In C\+\+\/CLI verwenden Sie die Makros CA\_SUPPRESS\_MESSAGE oder CA\_GLOBAL\_SUPPRESS\_MESSAGE in der Headerdatei, um das Attribut hinzuzufügen.  
  
 Sie dürfen keine Unterdrückungen im Quellcode in Releasebuilds verwenden, damit die Metadaten der Unterdrückung im Quellcode nicht versehentlich ausgeliefert werden.  Aufgrund des Verarbeitungsaufwands bei der Unterdrückung im Quellcode kann auch die Leistung der Anwendung beeinträchtigt werden, wenn die Metadaten der Unterdrückung im Quellcode eingeschlossen werden.  
  
> [!NOTE]
>  Diese Attribute müssen nicht manuell codiert werden.  Weitere Informationen finden Sie unter [Gewusst wie: Unterdrücken von Warnungen über das Menüelement](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  Das Menüelement ist für C\+\+\-Code nicht verfügbar.  
  
## SuppressMessage\-Attribut  
 Wenn Sie mit der rechten Maustaste in der **Fehlerliste** auf eine Codeanalysewarnung klicken und dann auf **Meldung\(en\) unterdrücken** klicken, wird entweder dem Code oder der globalen Unterdrückungsdatei des Projekts ein **SuppressMessage**\-Attribut hinzugefügt.  
  
 Das **SuppressMessage**\-Attribut verwendet folgendes Format:  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```c#  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 \[C\+\+\]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 Wobei:  
  
-   **Rule Category**: Die Kategorie, in der die Regel definiert wird.  Weitere Informationen zu Codeanalyseregeln finden Sie unter [Warnungen bei der Analyse von verwaltetem Code](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Rule Id**: Der Bezeichner der Regel.  Sowohl ein langer als auch ein kurzer Name für die Regel\-ID werden unterstützt.  Der kurze Name ist CAXXXX, der lange Name ist CAXXXX:FriendlyTypeName.  
  
-   **Justification**: Der Text, mit dem der Grund für die Unterdrückung der Meldung dokumentiert wird.  
  
-   **Message Id**: Der eindeutige Bezeichner eines Problems für die einzelnen Meldungen.  
  
-   **Scope**: Das Ziel, für das die Warnung unterdrückt wird.  Wenn kein Ziel angegeben wird, wird das Ziel des Attributs festgelegt.  Folgende Bereiche werden unterstützt:  
  
    -   Modul  
  
    -   Namespace  
  
    -   Ressource  
  
    -   Typ  
  
    -   Member  
  
-   **Target**: Ein Bezeichner, mit dem das Ziel angegeben wird, für das die Warnung unterdrückt wird.  Er muss einen vollständig qualifizierten Elementnamen enthalten.  
  
## Verwendung von SuppressMessage  
 Codeanalysewarnungen werden auf der Ebene unterdrückt, auf die eine Instanz des **SuppressMessage**\-Attributs angewendet wird.  Der Zweck besteht darin, die Unterdrückungsinformationen eng an den Code zu koppeln, in dem die Verletzung auftritt.  
  
 In der allgemeinen Form umfasst eine Unterdrückung die Regelkategorie sowie einen Regelbezeichner, der optional eine lesbare Darstellung des Regelnamens umfasst.  Beispiel:  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 Wenn die Metadaten für die Unterdrückung im Quellcode aus Gründen der Leistungsoptimierung minimiert werden müssen, kann der Regelname weggelassen werden.  Die Regelkategorie und die zugehörige Regel\-ID bilden zusammen einen hinreichend eindeutigen Regelbezeichner.  Beispiel:  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Dieses Format wird aufgrund von Problemen bei der Verwaltbarkeit nicht empfohlen.  
  
## Unterdrücken mehrerer Regelverletzungen in einem Methodentext  
 Attribute können nur für eine Methode übernommen und nicht in den Methodentext eingebettet werden.  Sie können den Bezeichner jedoch als Meldungs\-ID angeben, um mehrere Vorkommen einer Verletzung innerhalb einer Methode voneinander unterscheiden zu können.  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-cs[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## Generierter Code  
 Compiler für verwalteten Code und einige Tools von Drittanbietern generieren Code, um eine schnelle Codeentwicklung zu ermöglichen.  Vom Compiler generierter Code in Quelldateien wird normalerweise mit dem **GeneratedCodeAttribute**\-Attribut gekennzeichnet.  
  
 Sie können entscheiden, ob Codeanalysewarnungen und \-fehler für generierten Code unterdrückt werden sollen.  Informationen zum Unterdrücken dieser Warnungen und Fehler finden Sie unter [Gewusst wie: Unterdrücken von Warnungen für generierten Code](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Beachten Sie, dass **GeneratedCodeAttribute** von der Codeanalyse ignoriert wird, wenn es auf eine vollständige Assembly oder einen einzelnen Parameter angewendet wird.  Diese Situationen treten selten auf.  
  
## Unterdrückung auf globaler Ebene  
 Das Analysetool für verwalteten Code untersucht die **SuppressMessage**\-Attribute, die auf der Assembly\-, Modul\-, Typ\-, Member\- oder Parameterebene angewendet werden.  Zudem werden Verletzungen bei Ressourcen und Namespaces ausgelöst.  Diese Verletzungen müssen auf globaler Ebene angewendet werden und sind bereichs\- und zielbezogen.  Durch die folgende Meldung wird zum Beispiel eine Namespaceverletzung unterdrückt:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Wenn Sie eine Warnung mit Namespacebereich unterdrücken, wird die Warnung für den Namespace selbst unterdrückt.  Warnungen für Typen innerhalb des Namespaces werden nicht unterdrückt.  
  
 Jede Unterdrückung kann durch die Angabe eines expliziten Bereichs ausgedrückt werden.  Diese Art der Unterdrückung muss auf globaler Ebene erfolgen.  Sie können keine Unterdrückung auf Memberebene festlegen, indem Sie einen Typ ergänzen.  
  
 Unterdrückungen auf globaler Ebene sind die einzige Möglichkeit, Meldungen zu unterdrücken, die sich auf Code beziehen, der vom Compiler generiert wurde und sich keiner explizit angegebenen Benutzerquelle zuordnen lässt.  Mit dem folgenden Code wird z. B. eine Verletzung in Bezug auf einen vom Compiler ausgegebenen Konstruktor unterdrückt:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  Target enthält immer den vollständig qualifizierten Elementnamen.  
  
## Globale Unterdrückungsdatei  
 In der globalen Unterdrückungsdatei werden Unterdrückungen auf globaler Ebene bzw. Unterdrückungen ohne Ziel verwaltet.  So werden in dieser Datei z. B. Unterdrückungen auf Assemblyebene gespeichert.  Außerdem werden einige ASP.NET\-Unterdrückungen in dieser Datei gespeichert, da für Code, der einem Formular zugrunde liegt, keine Einstellungen auf Projektebene verfügbar sind.  Eine globale Unterdrückung wird erstellt und dem Projekt hinzugefügt, sobald im Fenster Fehlerliste die Option **In Projektunterdrückungsdatei** des Befehls **Meldung\(en\) unterdrücken** erstmalig ausgewählt wird.  Weitere Informationen finden Sie unter [Gewusst wie: Unterdrücken von Warnungen über das Menüelement](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## Siehe auch  
 <xref:System.Diagnostics.CodeAnalysis>