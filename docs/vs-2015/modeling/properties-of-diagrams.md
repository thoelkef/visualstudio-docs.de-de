---
title: Eigenschaften von Diagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31fb06512457f919b67d41c3fb4096e4c3477426
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652032"
---
# <a name="properties-of-diagrams"></a>Eigenschaften von Diagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Eigenschaften festlegen, die angeben, wie Diagramme im generierten Designer angezeigt werden. Beispielsweise können Sie im Diagramm eine Standardfarbe für Text angeben.

 Weitere Informationen finden Sie unter [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 In der folgenden Tabelle sind die Eigenschaften von Diagrammen aufgeführt.

|Eigenschaft|BESCHREIBUNG|Standard|
|--------------|-----------------|-------------|
|Füllfarbe|Die Füllfarbe für das Diagramm.|White|
|Textfarbe|Die Farbe des Texts, der im Diagramm angezeigt wird.|Schwarz|
|Zugriffsmodifizierer|Der Zugriffsmodifizierer der-Klasse (Public oder Internal).|Öffentlich|
|Benutzerdefinierte Attribute|Wird verwendet, um der generierten Code Klasse Attribute hinzuzufügen.|\<none>|
|Generiert doppelte abgeleitete|Gibt `True` an, dass sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert werden. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|Falsch|
|Hat benutzerdefinierten Konstruktor|Gibt `True` an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|Falsch|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die aus dem Diagramm generiert wird `none` ( `abstract` oder `sealed` ).|Keine|
|Basis Diagramm|Die Basisklasse dieses Diagramms.|(none)|
|Name|Der Name dieses Diagramms.|Aktueller Name|
|Namespace|Der Namespace, der mit diesem Diagramm verbunden ist.|Aktueller Namespace|
|Dargestellte Klasse|Die Stamm Domänen Klasse, die dieses Diagramm darstellt.|Aktuelle Stamm Klasse, falls zutreffend|
|Hinweise|Informelle Notizen, die diesem Element zugeordnet sind.|\<none>|
|Macht die Füllfarbe als Eigenschaft verfügbar.|Wenn `True` der Wert ist, kann der Benutzer die Füllfarbe des Diagramms des generierten Designers festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Form Diagramm, und klicken Sie auf **Hinzufügen**|Falsch|
|Macht Textfarbe als Eigenschaft verfügbar.|Wenn `True` der Wert ist, kann der Benutzer die Textfarbe des Diagramms im generierten Designer festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Form Diagramm, und klicken Sie auf **Hinzufügen**|Falsch|
|BESCHREIBUNG|Die Beschreibung, die zum Dokumentieren des generierten Designers verwendet wird.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für dieses Diagramm angezeigt wird.|\<none>|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für dieses Diagramm verwendet wird.|\<none>|

## <a name="see-also"></a>Weitere Informationen
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
