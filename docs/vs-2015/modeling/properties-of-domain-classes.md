---
title: Eigenschaften von Domänen Klassen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 91599e17fc132001de9fbb1a62a62918321a2dea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651995"
---
# <a name="properties-of-domain-classes"></a>Eigenschaften von Domänenklassen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domänen Klassen verfügen über die in der folgenden Tabelle aufgeführten Eigenschaften. Weitere Informationen zu Domänen Klassen finden Sie Untergrund Legendes zu [Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

|property|Beschreibung|Default|
|--------------|-----------------|-------------|
|Zugriffsmodifizierer|Die Zugriffsebene der Domänenklasse (`public` oder `internal`).|`public`|
|Benutzerdefinierte Attribute|Wird verwendet, um der Quell Code Klasse Attribute hinzuzufügen, die von dieser Domänen Klasse generiert werden.|\<none>|
|Generiert doppelte abgeleitete|Wenn `True`, werden sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, wird ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die von der Domänen Klasse generiert wird (`none`, `abstract` oder `sealed`).|`none`|
|Basisklasse|Wenn diese Domänen Klasse abgeleitet ist, der Name der Basisklasse.|\<none>|
|-Name|Der Name dieser Domänen Klasse.|Aktueller Name|
|Namespace|Der Namespace dieser Domänen Klasse.|Aktueller Namespace|
|Notizen|Informelle Notizen, die dieser Domänen Klasse zugeordnet sind.|\<none>|
|Beschreibung|Die Beschreibung, die verwendet wird, um die Benutzeroberfläche des generierten Designers zu dokumentieren.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für diese Domänen Klasse angezeigt wird.|\<none>|
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Domänen Klasse verwendet wird.|\<none>|

## <a name="see-also"></a>Siehe auch
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
