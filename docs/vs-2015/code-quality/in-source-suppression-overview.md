---
title: In der Übersicht über die Quelle Unterdrückung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 844681d079e5565aab9eceadb73f7d8a61cbb2c6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209039"
---
# <a name="in-source-suppression-overview"></a>Übersicht über die Unterdrückung im Quellcode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Unterdrückung im Quellcode ist die Möglichkeit, unterdrücken oder ignorieren Verletzungen der Codeanalyse in verwaltetem Code durch Hinzufügen der **SuppressMessage** -Attribut auf die Codesegmente, die dazu führen, die Verstöße dass. Die **SuppressMessage** -Attribut ist ein conditional-Attribut die in der IL-Metadaten einer Assembly mit verwaltetem Code enthalten ist, nur dann, wenn das Symbol für die CODE_ANALYSIS-Kompilierung zum Zeitpunkt der Kompilierung definiert wird.  
  
 In C++ / CLI, verwenden Sie die Makros, CA_SUPPRESS_MESSAGE oder CA_GLOBAL_SUPPRESS_MESSAGE in der Headerdatei, um das Attribut hinzuzufügen.  
  
 Sie sollten nicht im Quellcode-Unterdrückungen für Releasebuilds verwenden, um zu verhindern, dass die Metadaten für die Unterdrückung im Quellcode versehentlich zu versenden. Aufgrund der Verarbeitungskosten Unterdrückung im Quellcode kann auch die Leistung Ihrer Anwendung beeinträchtigt werden, durch die Unterdrückung im Quellcode-Metadaten einschließen.  
  
> [!NOTE]
>  Sie müssen zum Weitergeben Code diese Attribute selbst keine. Weitere Informationen finden Sie unter [wie: Unterdrücken von Warnungen über das Menüelement](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). Das Menüelement ist nicht für C++-Code verfügbar.  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage-Attributs  
 Wenn Sie mit der rechten Maustaste einer Codeanalyse-Warnung in der **Fehlerliste** , und klicken Sie dann auf **Nachrichten unterdrücken**, **SuppressMessage** Attribut hinzugefügt wird, in Ihrem Code oder auf der Globale Unterdrückungen-Datei des Projekts.  
  
 Die **SuppressMessage** Attribut weist das folgende Format:  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```csharp  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 [C++]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 Ort:  
  
-   **Regel Kategorie** -die Kategorie, in dem die Regel definiert wird. Weitere Informationen zu Codeanalyseregeln, finden Sie unter [Codeanalyse für verwalteten Code (Warnungen)](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Regel-Id** – der Bezeichner der Regel. Die Unterstützung umfasst sowohl eine kurze und lange Namen für die Regel-ID an. Der kurze Name ist CAXXXX; der lange Name ist CAXXXX:FriendlyTypeName.  
  
-   **Begründung** -der Text, der verwendet wird, um den Grund für das Unterdrücken der Meldung dokumentieren.  
  
-   **Meldungs-Id** – Eindeutiger Bezeichner für ein Problem für jede Nachricht.  
  
-   **Bereich** -Ziel auf dem die Warnung unterdrückt wird. Wenn das Ziel nicht angegeben ist, wird es an das Ziel des Attributs festgelegt. Die folgenden: Bereiche werden unterstützt  
  
    -   Modul  
  
    -   Namespace  
  
    -   Ressource  
  
    -   Typ  
  
    -   Member  
  
-   **Ziel** – ein Bezeichner, der verwendet wird, an das Ziel, auf dem die Warnung unterdrückt wird. Es muss einen vollqualifizierten Elementnamen enthalten.  
  
## <a name="suppressmessage-usage"></a>SuppressMessage-Nutzung  
 Warnungen der Codeanalyse unterdrückt werden, auf der Ebene, der eine Instanz von der **SuppressMessage** Attribut angewendet wird. Das Zweck dieses werden eng gekoppelt die Unterdrückungsinformationen aus, um den Code, in dem die Verletzung auftritt.  
  
 Die allgemeine Form der Unterdrückung umfasst die Regelkategorie und eine optionale lesbare Darstellung der Regelname enthält Regelbezeichner. Ein auf ein Objekt angewendeter  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 Treten strict Leistungsgründen Unterdrückung im Quellcode-Metadaten zu minimieren, kann der Regelnamen selbst außer acht gelassen werden. Die Regelkategorie und die Regel-ID bilden zusammen einen ausreichend eindeutigen Regelbezeichner. Ein auf ein Objekt angewendeter  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Dieses Format wird aufgrund von Problemen mit Verwaltbarkeit nicht empfohlen.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Mehrere Verstöße innerhalb eines Methodentexts unterdrücken  
 Attribute können nur auf eine Methode angewendet werden und können nicht innerhalb des Methodentexts eingebettet werden. Allerdings können Sie den Bezeichner als die Nachrichten-ID, um mehrere Vorkommen eines Verstoßes innerhalb einer Methode zu unterscheiden angeben.  
  
 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]  
  
## <a name="generated-code"></a>Generierter Code  
 Compiler für verwalteten Code und einige Tools von Drittanbietern generieren Code aus, um die schnelle Codeentwicklung zu ermöglichen. Vom Compiler generierter Code, der in Quelldateien angezeigt wird, ist in der Regel mit markiert die **GeneratedCodeAttribute** Attribut.  
  
 Sie können auswählen, ob codeanalysewarnungen und-Fehler für generierten Code zu unterdrücken. Informationen dazu, wie Sie solche Warnungen und Fehler unterdrücken, finden Sie unter [wie: Unterdrücken von Warnungen für generierten Code](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Beachten Sie, bei der Codeanalyse ignoriert **GeneratedCodeAttribute** Wenn es auf eine gesamte Assembly oder einen einzelnen Parameter angewendet wird. Diese Situationen treten selten auf.  
  
## <a name="global-level-suppressions"></a>Unterdrückungen auf Projektebene globale  
 Das Analysetool für verwalteten Code untersucht **SuppressMessage** Attribute, die Ebene der Assembly, Modul, Typ, Member oder Parameter angewendet werden. Es wird auch ausgelöst, Verstöße gegen Ressourcen und Namespaces. Diese Verletzungen sind auf globaler Ebene angewendet werden muss und begrenzt und ausgerichtet. Die folgende Meldung wird z. B. eine Namespaceverletzung unterdrückt:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Wenn Sie eine Warnung mit dem Namespace-Gültigkeitsbereich unterdrücken, unterdrückt sie die Warnung für den Namespace selbst. Unterdrückt nicht die Warnung für Typen im Namespace.  
  
 Durch einen expliziten Bereich angeben, kann jede Unterdrückung ausgedrückt werden. Diese Unterdrückungen müssen auf globaler Ebene befinden. Sie können nicht auf Memberebene Unterdrückung angeben, durch das ergänzen eines Typs.  
  
 Unterdrückungen auf Projektebene Global sind die einzige Möglichkeit, Nachrichten zu unterdrücken, die auf die vom Compiler generierter Code verweisen, die nicht explizit angegebenen Benutzerquelle zugeordnet ist. Der folgende Code unterdrückt z. B. einen Verstoß gegen einen Compiler ausgegebenen Konstruktor:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  Target enthält immer den vollqualifizierten Namen.  
  
## <a name="global-suppression-file"></a>Globale Unterdrückungsdatei  
 Der globale Unterdrückungsdatei verwaltet Unterdrückungen, die entweder auf globaler Ebene Unterdrückungen oder Unterdrückungen, die kein Ziel angeben. Unterdrückungen auf Verletzungen der Assembly werden z. B. in dieser Datei gespeichert. Darüber hinaus werden einige ASP.NET Unterdrückungen in dieser Datei gespeichert, da projekteinstellungen nicht für Code für ein Formular verfügbar sind. Eine globale Unterdrückungsdatei erstellt und hinzugefügt zu Ihrem Projekt zum ersten Mal, die Sie auswählen der **In Projektunterdrückungsdatei** Möglichkeit, die **Nachrichten unterdrücken** Befehl in das Fenster "Fehlerliste". Weitere Informationen finden Sie unter [wie: Unterdrücken von Warnungen über das Menüelement](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Diagnostics.CodeAnalysis>



