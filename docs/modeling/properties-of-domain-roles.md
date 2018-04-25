---
title: Eigenschaften von Domänenrollen
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ead7128c998b8c4ed97acac0f6da0f08113e7bef
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="properties-of-domain-roles"></a>Eigenschaften von Domänenrollen
Die Eigenschaften in der folgenden Tabelle sind die einer Domäne zugewiesen. Informationen zu Funktionen finden Sie unter [Grundlegendes zu Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Eigenschaft|Beschreibung|Standard|
|--------------|-----------------|-------------|
|"Sammlung"|Diese Rolle verfügt eine Multiplizität von 0.. * oder 1... \*, diese Eigenschaft passt den generischen Typ, der verwendet wird, um die Auflistung von Links zu speichern.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> wird verwendet|
|Benutzerdefinierte Attribute|Attribute, die Sie hier angeben, werden als Attribute der generierte Code-Klasse hinzugefügt werden.|< keine\>|
|Ist die Eigenschaft durchsucht werden kann|Wenn `True`, und wenn die Multiplizität der Beziehung 0.. 1 oder 1..1 ist, kann die Rolle ""-Eigenschaft durchsucht werden, vom Benutzer in der **Eigenschaften** Fenster. Die Eigenschaft zeigt den Namen des Elements am anderen Ende der Beziehung-Verknüpfung an.|`True`|
|Ist die Eigenschaft-Generator|Wenn `True`, eine Rolleneigenschaft ist für diese Rolle, die Sie verwenden können, um die Beziehung im Programmcode durchlaufen generiert. Wenn Sie diese Einstellung "false" festlegen, können Sie die Beziehung in einer weniger effiziente Weise durchlaufen, mithilfe von statischen Methoden der domänenbeziehung.|`True`|
|Eigenschaft Getter-Zugriffsmodifizierer|Der Zugriffsmodifizierer für die Getter-Methode für die generierte Eigenschaft (`public`, `internal`, `private`, `protected`, oder `protected internal`).|`public`|
|Eigenschaft-Setter-Zugriffsmodifizierer|Der Zugriffsmodifizierer für den Setter für die generierte Eigenschaft (`public`, `internal`, `private`, `protected`, oder `protected internal`).|`public`|
|Multiplizität|Die Anzahl der betroffenen Modellelemente die entgegengesetzte Rolle spielen können (`0..1`, `1..1`, `0..*`, oder `1..*`). Wenn die Multiplizität ist `0..*` oder `1..*`, klicken Sie dann die generierte Eigenschaft stellt eine Auflistung dar; die generierte Eigenschaft darstellt, andernfalls ein einzelnes Modell-Element.|Richtet sich nach den Beziehungstyp und, ob dies die Quelle oder Ziel-Rolle in der Beziehung ist.|
|Name|Der Name der Rolle "Domäne". Diese Eigenschaft darf kein Leerzeichen enthalten.|Der Name der Domänenklasse für die Rolleninhaber für diese Rolle.|
|Gibt die Kopie weiter|`DoNotPropagateCopy` – Die Rolle "kopiert" Player müssen keine Kopie des Links.<br /><br /> `PropagateCopyToLinkOnly` – Der kopierte Link verweist auf den vorhandenen entgegengesetzten Rolleninhaber.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` – Der kopierte Link verweist auf eine Kopie der entgegengesetzten Rolleninhaber.|`PropagateCopyToLinkAndOppositeRolePlayer` für die Quellrollen von eingebetteten Objekten.<br /><br /> `DoNotPropagateCopy` für andere Rollen.<br /><br /> Weitere Informationen finden Sie unter [Kopierverhalten anpassen](../modeling/customizing-copy-behavior.md)|
|Verteilt löschen|`True` So löschen Sie das Element, das dieser Rolle spielt, wenn Sie der entsprechenden Link gelöscht wird.|`True` für das Ziel einer Rolle einbetten.<br /><br /> `False` für andere Rollen.<br /><br /> Weitere Informationen finden Sie unter [anpassen, löschen Sie das Verhalten](../modeling/customizing-deletion-behavior.md).|
|Eigenschaftenname|Der Name der Eigenschaft, die in den Code für die Rolleninhaber generiert. Dieser Name darf keine Leerzeichen enthalten.|Der Name der entgegengesetzten Rolle verfügt diese Rolle eine 0 (null): 1- oder eine 1: 1 Multiplizität; andernfalls der pluralized Name der entgegengesetzten Rolle.|
|Rolleninhaber|Die Domänenklasse des Elements, das diese Rolle in der Beziehung einnehmen kann. Diese Eigenschaft ist schreibgeschützt.|Die Domänenklasse, der die Rolleninhaber für diese Rolle werden soll.|
|Notizen|Informelle Hinweise, die mit der Domäne verknüpft sind.|< keine\>|
|Kategorie|Die Kategorie, unter denen die generierte Eigenschaft angezeigt, in wird, der **Eigenschaften** Fenster im generierten Designer. Wenn diese Eigenschaft leer ist, wird die generierte Eigenschaft angezeigt, unter wird dem **Verschiedenes** Kategorie|< keine\>|
|Beschreibung|Die Beschreibung, die wird verwendet, um Code zu dokumentieren und in der Benutzeroberfläche des Designers generierten verwendet.<br /><br /> Die Beschreibung wird in der IntelliSense-QuickInfo für die generierte Eigenschaft für die Rolle Player-Klasse.|`Description for` *der vollständige Name der Rolle*|
|Anzeigename|Der Name, der in der generierten Designer für die Rolle "Domäne" angezeigt wird.|Der angepasste Wert der Name-Eigenschaft.|
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für die Rolle "Domäne" verwendet wird.|\<keine >|
|Anzeigename der Eigenschaft|Der Name, der in der generierten Designer für die Rolle "generierten" Eigenschaft angezeigt wird.|Der angepasste Wert der Eigenschaftsname-Eigenschaft.|

> [!NOTE]
> Der Standardwert, der einen Anzeigenamen basiert auf den Wert der zugehörigen Eigenschaft durch Einfügen von Leerzeichen vor dem jedes Zeichen Großbuchstaben, Kleinbuchstaben Zeichen vorangestellt ist und nicht gefolgt vom anderen Großbuchstaben.

## <a name="see-also"></a>Siehe auch

- [Eigenschaften von Domänenbeziehungen](../modeling/properties-of-domain-relationships.md)