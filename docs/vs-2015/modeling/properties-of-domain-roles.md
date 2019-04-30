---
title: Eigenschaften von Domänenrollen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b78c409a761a98439cbbbfdf088e052eca745f32
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444469"
---
# <a name="properties-of-domain-roles"></a>Eigenschaften von Domänenrollen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Eigenschaften in der folgenden Tabelle sind einer Domäne zugewiesen. Weitere Informationen zu den Funktionen der Domäne, finden Sie unter [Grundlegendes zu Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|Auflistungstyp|Wenn diese Rolle eine Multiplizität von 0 aufweist. * oder 1... \*, dieser Eigenschaft passt den generische Typ, der verwendet wird, um die Auflistung von Links zu speichern.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> wird verwendet|  
|Benutzerdefinierte Attribute|Attribute, die Sie hier angeben, werden als Attribute der generierten Codeklasse hinzugefügt werden.|\<none>|  
|Ist die Eigenschaft durchsucht werden kann|Wenn `True`, und wenn die Multiplizität der Beziehung 0.. 1 "oder" 1..1 ist, kann die Role-Eigenschaft durchsucht werden, vom Benutzer in der **Eigenschaften** Fenster. Die Eigenschaft zeigt den Namen des Elements am anderen Ende des beziehungslinks.|`True`|  
|Eigenschaft-Generator ist|Wenn `True`, eine Rolleneigenschaft ist für diese Rolle, die Sie, zum Durchlaufen der Beziehung im Programmcode verwenden können generiert. Wenn Sie diese "false" festlegen, können Sie die Beziehung auf eine weniger effiziente Weise durchlaufen, mithilfe der statische Methoden der domänenbeziehung.|`True`|  
|Eigenschaft Getter-Zugriffsmodifizierer|Der Zugriffsmodifizierer für den Getter für die generierte Eigenschaft (`public`, `internal`, `private`, `protected`, oder `protected internal`).|`public`|  
|Eigenschaft-Setter-Zugriffsmodifizierer|Der Zugriffsmodifizierer für den Setter für die generierte Eigenschaft (`public`, `internal`, `private`, `protected`, oder `protected internal`).|`public`|  
|Multiplizität|Die Anzahl der Modellelemente, die die entgegengesetzte Rolle spielen kann (`0..1`, `1..1`, `0..*`, oder `1..*`). Wenn die Multiplizität `0..*` oder `1..*`, klicken Sie dann die generierte Eigenschaft stellt eine Auflistung; andernfalls die generierte Eigenschaft stellt ein einzelnes Modell-Element dar.|Hängt von der Art der Beziehung und ob es sich um die Quelle oder Ziel-Rolle in der Beziehung handelt.|  
|Name|Der Name der Rolle "Domäne". Diese Eigenschaft kann keine Leerzeichen enthalten.|Der Name der Domänenklasse für den Rolleninhaber für diese Rolle.|  
|Überträgt die Kopie|`DoNotPropagateCopy` – Die kopierte Rolleninhaber müssen keine Kopie dieses links.<br /><br /> `PropagateCopyToLinkOnly` – Die kopierte Link verweist auf die vorhandene Gegenrolle.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` – Der kopierte Link verweist auf eine Kopie der Gegenrolle.|`PropagateCopyToLinkAndOppositeRolePlayer` für die Quellrollen der einbettungen.<br /><br /> `DoNotPropagateCopy` für andere Rollen.<br /><br /> Weitere Informationen finden Sie unter [Anpassen des Verhaltens beim Kopieren](../modeling/customizing-copy-behavior.md)|  
|Überträgt löschen|`True` um das Element zu löschen, das dieser Rolle spielt, wenn Sie der entsprechenden Link gelöscht wird.|`True` für das Ziel einer einbettenden Rolle.<br /><br /> `False` für andere Rollen.<br /><br /> Weitere Informationen finden Sie unter [Anpassen des Löschverhaltens](../modeling/customizing-deletion-behavior.md).|  
|Eigenschaftenname|Der Name der Eigenschaft in den Code für den Rolleninhaber generiert werden soll. Dieser Name darf keine Leerzeichen enthalten.|Der Name der entgegengesetzten Rolle dieser Rolle besitzt eine 0 (null): 1- oder eine 1: 1-Multiplizität; andernfalls der pluralisierte Name der entgegengesetzten Rolle.|  
|Rolleninhaber|Die Domänenklasse des Elements, das diese Rolle in der Beziehung einnehmen kann. Diese Eigenschaft ist schreibgeschützt.|Die Domänenklasse der Zielrolleninhaber für diese Rolle.|  
|Hinweise|Informelle Hinweise, die mit die Rolle zugewiesen sind.|\<none>|  
|Kategorie|Die Kategorie, unter der die generierte Eigenschaft angezeigt, in wird, der **Eigenschaften** Fenster im generierten Designer. Wenn diese Eigenschaft leer ist, und klicken Sie dann die generierte Eigenschaft angezeigt, unter wird dem **Verschiedenes** Kategorie|\<none>|  
|Beschreibung|Die Beschreibung, die wird verwendet, um Code zu dokumentieren, die in der Benutzeroberfläche des generierten Designers verwendet wird.<br /><br /> Die Beschreibung wird in der Intellisense-QuickInfo für die der rolleninhaberklasse generierten Eigenschaft.|`Description for` *der vollständige Name der Rolle*|  
|Anzeigename|Der Name, der im generierten Designer für die Domänenrolle angezeigt wird.|Der angepasste Wert der Name-Eigenschaft.|  
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für die Domänenrolle verwendet wird.|\<none>|  
|Anzeigename der Eigenschaft|Der Name, der im generierten Designer für die Eigenschaft der generierten Rolle angezeigt wird.|Der angepasste Wert der Eigenschaftenname-Eigenschaft.|  
  
> [!NOTE]
> Der Standardwert, der einen Anzeigenamen basiert auf der zugehörige Eigenschaftswert durch Einfügen von Leerzeichen vor jeder-Großbuchstaben, einen Kleinbuchstaben Zeichen vorangestellt ist und nicht ein anderes Großbuchstaben Zeichen folgt.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften von Domänenbeziehungen](../modeling/properties-of-domain-relationships.md)
