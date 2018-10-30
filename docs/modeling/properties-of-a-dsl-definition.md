---
title: Eigenschaften einer DSL-Definition
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 990b55f4ba78f32acba40c325ade596f5628c54f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893935"
---
# <a name="properties-of-a-dsl-definition"></a>Eigenschaften einer DSL-Definition
DslDefinition-Eigenschaften wird definiert, *Domain-Specific Languge* Eigenschaften wie z. B. versionsnummerierung Definition. DslDefinition Eigenschaften werden in der **Eigenschaften** anzeigen, wenn Sie einen offenen Bereich des Diagramms im klicken Sie auf die *domänenspezifischen Sprachdesigner*.

 Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition hat die Eigenschaften in der folgenden Tabelle:

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|Zugriffsmodifizierer|Bestimmt, ob der Zugriffsmodifizierer für die Domänenklasse öffentlich oder intern ist.|public|
|Benutzerdefinierte Attribute|Benutzerdefinierter Attribute für die Domänenklasse.<br /><br /> **Beachten Sie** verwenden Sie die Schaltfläche zum Durchsuchen, um ein Attribut hinzuzufügen.|\<Keine >|
|Firmenname|Der Name des aktuellen Unternehmensnamens in der systemregistrierung.|Aktuelle Unternehmensname|
|name|Der Name dieser Domänenklasse.|Aktuelle name|
|Namespace|Mit dieser Domäne verbundene den Namespace.|Aktuellen namespace|
|Paket-Guid|Die Guid für das für diese DSL generierte Visual Studio-Paket.|\<Keine >|
|Paket-Namespace|Der Namespace für das für diese DSL generierte Visual Studio-Paket.|\<Keine >|
|Produktname|Der Name des Produkts, das für das für diese DSL generierte Visual Studio-Paket registriert wird.|\<Keine >|
|Hinweise|Anmerkungen im Zusammenhang mit dieser Domänenklasse.|\<Keine >|
|Beschreibung|Die Beschreibung dieser Domänenklasse.|\<Keine >|
|Anzeigename|Der Name, der im generierten Designer für diese Domänenklasse angezeigt wird.|\<Keine >|
|Hilfsschlüsselwort|Das Hilfeschlüsselwort, das mit dieser Domäne verknüpft ist.|\<Keine >|
|Build|Die Anzahl der inkrementelle Builds für diese Definition einer domänenspezifischen Sprache.|0|
|Hauptversion|Die inkrementelle Hauptbuildnummer für diese Definition einer domänenspezifischen Sprache.|1|
|Nebenversion|Die Anzahl der inkrementellen Nebenversionsnummer des Builds für diese Definition einer domänenspezifischen Sprache.|0|
|Revision|Die inkrementelle Revision Buildnummer für diese Definition einer domänenspezifischen Sprache.|0|

## <a name="see-also"></a>Siehe auch

- [DSL-Tools – Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)