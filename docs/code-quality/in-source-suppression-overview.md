---
title: "In Datenquelle unterdrückenden (Übersicht) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92babbf3c7a5863d178463b69525bdb722bf28ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="in-source-suppression-overview"></a>Übersicht über die Unterdrückung im Quellcode
Unterdrückung im Quellcode ist die Fähigkeit, unterdrückt oder ignoriert Verletzungen der Codeanalyse in verwaltetem Code durch Hinzufügen der **SuppressMessage** -Attribut auf die Codesegmente, die dazu führen, die Verstöße dass. Die **SuppressMessage** -Attribut ist ein conditional-Attribut das in der IL-Metadaten einer Assembly mit verwaltetem Code enthalten ist, nur dann, wenn zum Zeitpunkt der Kompilierung die CODE_ANALYSIS-Kompilierungssymbol definiert ist.  
  
 In C + c++ / CLI, verwenden Sie die Makros CA_SUPPRESS_MESSAGE oder CA_GLOBAL_SUPPRESS_MESSAGE in der Headerdatei, um das Attribut hinzuzufügen.  
  
 Sie sollten die Unterdrückung im Quellcode nicht auf Releasebuilds verwenden, um zu verhindern, dass die Unterdrückung im Quellcode Metadaten versehentlich Protokollversand. Aufgrund der Verarbeitungskosten Unterdrückung im Quellcode kann die Leistung Ihrer Anwendung auch durch die Unterdrückung im Quellcode Metadaten einschließlich beeinträchtigt sein.  
  
> [!NOTE]
>  Sie müssen zur hand Code diese Attribute selbst keine. Weitere Informationen finden Sie unter [wie: Unterdrücken von Warnungen über das Menüelement](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). Das Menüelement ist nicht verfügbar für C++-Code.  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage-Attribut  
 Wenn Sie mit der rechten Maustaste in einer Codeanalyse Warnung die **Fehlerliste** , und klicken Sie dann auf **Meldung(en) unterdrücken**, **SuppressMessage** Attribut hinzugefügt wird, im Code oder auf der Globale Unterdrückungen-Datei des Projekts.  
  
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
  
-   **Regel "Kategorie"** – die Kategorie aus, in dem die Regel definiert wird. Weitere Informationen zu Codeanalyseregeln, finden Sie unter [Codeanalyse für verwalteten Code (Warnungen)](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Regel-Id** -der Bezeichner der Regel. Unterstützung umfasst sowohl einen kurz- und langfristigen Namen für die Regel-ID an. Der kurze Name ist CAXXXX; der lange Name ist CAXXXX:FriendlyTypeName.  
  
-   **Durch den Blocksatz** -der Text, der verwendet wird, um den Grund für die Unterdrückung der Meldung dokumentieren.  
  
-   **Meldungs-Id** -eindeutige Bezeichner für ein Problem für jede Nachricht.  
  
-   **Bereich** -Ziel, auf dem die Warnung unterdrückt wird. Wenn das Ziel nicht angegeben ist, wird er auf das Ziel des Attributs festgelegt. Die folgenden: Bereiche werden unterstützt  
  
    -   Modul  
  
    -   Namespace  
  
    -   Ressource  
  
    -   Typ  
  
    -   Member  
  
-   **Ziel** : ein Bezeichner, der verwendet wird, um das Ziel anzugeben, auf dem die Warnung unterdrückt wird. Sie müssen einen vollständig qualifizierten Elementnamen enthalten.  
  
## <a name="suppressmessage-usage"></a>SuppressMessage-Verwendung  
 Codeanalysewarnungen unterdrückt werden, auf der Ebene, der eine Instanz von der **SuppressMessage** Attribut angewendet wird. Das Zweck dieses werden eng gekoppelt die Unterdrückungsinformationen an den Code, in dem die Verletzung auftritt.  
  
 Das allgemeine Format Unterdrückung umfasst die Regelkategorie und Regelbezeichner enthält eine optionale lesbare Darstellung des Regelnamens. Ein auf ein Objekt angewendeter  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 Treten strict aus Leistungsgründen für die Unterdrückung im Quellcode Metadaten zu minimieren, kann der Regelnamen selbst außer acht gelassen werden. Die Regelkategorie und die zugehörige Regel-ID bilden zusammen hinreichend eindeutigen Regelbezeichner. Ein auf ein Objekt angewendeter  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Dieses Format wird nicht aufgrund von Verbindungsproblemen Verwaltbarkeit empfohlen.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Mehrere Verstöße innerhalb eines Methodentexts unterdrücken  
 Attribute können nur auf eine Methode angewendet werden und können nicht innerhalb des Methodentexts eingebettet werden. Allerdings können Sie den Bezeichner als die Nachrichten-ID, um mehrere Vorkommen eines Verstoßes innerhalb einer Methode zu unterscheiden angeben.  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-csharp[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## <a name="generated-code"></a>Generierter Code  
 Compiler für verwalteten Code und einige Drittanbieter-Tools generieren Code aus, um eine schnelle Codeentwicklung zu ermöglichen. Vom Compiler generierte Code, der in Quelldateien ist in der Regel mit markiert die **GeneratedCodeAttribute** Attribut.  
  
 Sie können auswählen, ob das Unterdrücken von codeanalysewarnungen und Fehler für generierten Code. Weitere Informationen dazu, wie solche Warnungen und Fehler unterdrücken, finden Sie unter [wie: Unterdrücken von Warnungen für generierten Code](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Beachten Sie, die Codeanalyse ignoriert **GeneratedCodeAttribute** Wenn sie eine gesamte Assembly oder einen einzelnen Parameter angewendet wird. Diese Situationen treten selten auf.  
  
## <a name="global-level-suppressions"></a>Auf globaler Ebene Unterdrückungen  
 Die verwaltete Codeanalysetool überprüft **SuppressMessage** Attribute, die auf die Assembly, Modul, Typ, Member oder ein Parameterwert Ebene angewendet werden. Es wird auch ausgelöst, Verstöße gegen die Ressourcen und Namespaces. Diese Verstöße wurden auf globaler Ebene angewendet werden muss und im Bereich einer und angewendet. Die folgende Meldung unterdrückt z. B. einen Namespace Verstoß:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Wenn Sie eine Warnung mit Namespacebereich unterdrücken, wird die Warnung für den Namespace selbst unterdrückt. Sie unterdrückt die Warnung für Typen im Namespace nicht.  
  
 Jede Unterdrückung kann durch Angabe eines expliziten Bereichs ausgedrückt werden. Diese Unterdrückungen müssen auf globaler Ebene befinden. Sie können nicht auf Memberebene Unterdrückung werden, indem einen Typ angeben.  
  
 Auf globaler Ebene Unterdrückungen sind die einzige Möglichkeit, Nachrichten zu unterdrücken, die vom Compiler generierte Code verweisen, die explizit angegebene Benutzerquelle zugeordnet ist. Der folgende Code unterdrückt z. B. einen Verstoß gegen einen Konstruktor Compiler ausgegeben:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  Target enthält immer den vollqualifizierten Elementnamen.  
  
## <a name="global-suppression-file"></a>Globale Unterdrückungsdatei  
 Die Unterdrückungsdatei für die globale verwaltet Unterdrückungen, die auf globaler Ebene Unterdrückungen oder Unterdrückungen, die kein Ziel angeben. Beispielsweise werden Unterdrückungen für Verletzungen der Assembly in dieser Datei gespeichert. Darüber hinaus sind einige Unterdrückungen ASP.NET in dieser Datei gespeichert, da Ebene projekteinstellungen nicht für Code für ein Formular verfügbar sind. Eine globale Unterdrückung erstellt und hinzugefügt zu Ihrem Projekt zum ersten Mal, die Sie auswählen der **im Projektunterdrückungsdatei** -Option von der **Meldung(en) unterdrücken** -Befehl im Fenster "Fehlerliste". Weitere Informationen finden Sie unter [wie: Unterdrücken von Warnungen über das Menüelement](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Diagnostics.CodeAnalysis>