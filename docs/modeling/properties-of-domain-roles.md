---
title: "Eigenschaften von Dom&#228;nenrollen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 9
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 9
---
# Eigenschaften von Dom&#228;nenrollen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Eigenschaften in der folgenden Tabelle sind mit einer Rolle verbundenen Domänen.  Weitere Informationen über Domänen, finden Sie unter [Grundlagen von Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md).  Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)verwendet.  
  
|Property|Beschreibung|Standardwert|  
|--------------|------------------|------------------|  
|Auflistungs\-Typ|Wenn diese Rolle Multiplizität von 0 aufweist. \* oder 1. \*, stimmt diese Eigenschaft den generischen Typ an, der verwendet wird, um die Auflistung von Links zu speichern.|`(none)`\- <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> verwendet wird|  
|Benutzerdefinierte Attribute|Attribute, die Sie hier angeben, werden als Attribute für die generierte Codeklasse hinzugefügt.|\<Keine\>|  
|Ist der browsebare Eigenschaft|Wenn kann `True`und wenn die Multiplizität der Beziehung 0..1 oder 1..1 befindet, die Rolle Eigenschaft vom Benutzer im **Eigenschaften** Fenster durchsucht werden.  Die Eigenschaft enthält den Namen des Elements am anderen Ende der Verhältnis\-Links an.|`True`|  
|Ist Eigenschaft\-Generator|Wenn `True`, eine Rolle Eigenschaft für diese Rolle generiert wird, die Sie verwenden können, um die Beziehung im Programmcode zu durchlaufen.  Wenn Sie diesen Wert false ist, rufen Sie die Beziehung in einer weniger effiziente Weise durchlaufen werden können, indem statische Methoden des Domänen\-Verhältnisses verwenden.|`True`|  
|Eigenschaft\-Getter\-Zugriffsmodifizierer|Der Zugriffsmodifizierer für den Getter für die generierte Eigenschaft \(`public`, `internal`, `private`, `protected`oder `protected internal`\).|`public`|  
|Eigenschaft\-Setzer\-Zugriffsmodifizierer|Der Zugriffsmodifizierer für den Setter für die generierte Eigenschaft \(`public`, `internal`, `private`, `protected`oder `protected internal`\).|`public`|  
|Multiplizität|Die Anzahl von Modellelementen, die die entgegengesetzte Rolle \(`0..1`, `1..1`, `0..*`oder `1..*`\) ausgeführt werden können.  Wenn die Multiplizität `0..*` oder `1..*`ist, enthält die generierte Eigenschaft eine Auflistung dar. andernfalls stellt die generierte Eigenschaft ein einzelnes Modellelement dar.|Hängt vom Beziehungstyp ab und davon, ob dies die Quell\- oder Zielrolle relativ ist.|  
|Name|Der Name der Rolle Domänen.  Diese Eigenschaft kann Leerzeichen enthalten.|Der Name der Domänenklasse der Rolle Players für diese Rolle.|  
|Kopieren Verbreitet|`DoNotPropagateCopy` \- die kopierte Rolle Player verfügt über keine Kopie des Links.<br /><br /> `PropagateCopyToLinkOnly` kopierten \- Der Link verweist auf den vorhandenen Rolle von der Spieler.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`kopierten \- Der Link verweist auf eine Kopie der entgegengesetzten Rolle Players.|`PropagateCopyToLinkAndOppositeRolePlayer` für die Quellspalten der Bildlauf embeddings.<br /><br /> `DoNotPropagateCopy` für andere Rollen.<br /><br /> Weitere Informationen finden Sie unter [Anpassen des Kopierverhaltens](../modeling/customizing-copy-behavior.md)|  
|Verbreitet Löschen|`True` , um das Element zu löschen, das diese Rolle spielt, wenn der zugeordnete Link gelöscht wird.|Mithilfe von eingebetteten`True` für das Ziel einer Rolle.<br /><br /> `False` für andere Rollen.<br /><br /> Weitere Informationen finden Sie unter [Anpassen des Löschverhaltens](../modeling/customizing-deletion-behavior.md).|  
|Eigenschaftenname|Der Name der Eigenschaft im Code generiert der Rolle Players.  Dieser Name darf keine Leerzeichen enthalten.|Der Name der entgegengesetzten Rolle, wenn diese Rolle verfügt oder eine null\-zu\-ein 1:1 Multiplizität; Andernfalls ist der pluralized Name der entgegengesetzten Rolle.|  
|Rolle Player\-|Die Domänenklasse des Elements, das diese Rolle in der Beziehung einnehmen kann.  Diese Eigenschaft ist schreibgeschützt.|Die Domänenklasse der Rolle Players für diese Rolle.|  
|Hinweise|Informelle Hinweise, die der Rolle zugeordnet sind, Domänen.|\<Keine\>|  
|Kategorie|Die Kategorie, unter der die generierte Eigenschaft im **Eigenschaften** Fenster im generierten Designer angezeigt wird.  Wenn diese Eigenschaft leer ist, wird die generierte Eigenschaft mit der **Sonstiges** Kategorie|\<Keine\>|  
|Beschreibung|Die Beschreibung, die dem Code für Dokumente verwendet wird und in der Benutzeroberfläche des generierten Designers verwendet wird.<br /><br /> Die Beschreibung wird in der IntelliSense\-QuickInfo für die generierte Eigenschaft für die Rolle Player Klasse.|`Description for` *der vollständige Name der Rolle*|  
|Angezeigter Name|Der Name, der im generierten Rolle für die Domänen Designer angezeigt wird.|Der angepasste Wert der Name\-Eigenschaft.|  
|Hilfeschlüsselwort|Das optionale Schlüsselwort, das zur Rolle für die Domänen F1\-Hilfe Index verwendet wird.|\<Keine\>|  
|Eigenschaft\-Anzeigename|Der Name, der im generierten Designer für die generierte Rolle Eigenschaft angezeigt wird.|Der angepasste Wert der Eigenschaftennamen der Eigenschaft.|  
  
> [!NOTE]
>  Der Standardwert des Anzeigenamens basiert auf der zugehörige Eigenschaftswert, indem er Leerzeichen vor jedem Großbuchstaben einfügt, der von einem Kleinbuchstaben vorangestellt ist und nicht von einem anderen Großbuchstaben folgt.  
  
## Siehe auch  
 [Eigenschaften von Domänenbeziehungen](../modeling/properties-of-domain-relationships.md)