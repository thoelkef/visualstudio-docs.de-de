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
ms.openlocfilehash: be119703868316f2335f06174c9f21c2dddd2edc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="properties-of-a-dsl-definition"></a>Eigenschaften einer DSL-Definition
DslDefinition Eigenschaften definieren *einer domänenspezifischen Sprache* Definitionseigenschaften z. B. versionsnummerierung. DslDefinition Eigenschaften werden in der **Eigenschaften** Fenster, wenn Sie auf einen offenen Bereich des Diagramms in die *einer domänenspezifischen Sprachdesigner*.

 Weitere Informationen finden Sie unter [zum Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition verfügt über die Eigenschaften in der folgenden Tabelle:

|Eigenschaft|Beschreibung|Standard|
|--------------|-----------------|-------------|
|Zugriffsmodifizierer|Bestimmt, ob der Zugriffsmodifizierer für die Domänenklasse öffentliche oder eine interne ist.|public|
|Benutzerdefinierte Attribute|Benutzerdefinierte definiert die Attribute für die Domänenklasse.<br /><br /> **Hinweis** verwenden Sie die Schaltfläche zum Durchsuchen, um ein Attribut hinzuzufügen.|\<keine >|
|Firmenname|Der Name des aktuellen Unternehmensnamens in der systemregistrierung.|Aktuelle Firmenname|
|name|Der Name dieser Domäne-Klasse.|Aktuelle name|
|Namespace|Der Namespace zugeordnet ist diese Domänenklasse.|Aktuellen namespace|
|Paket-Guid|Die Guid für die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Paket für diese DSL generiert.|\<keine >|
|Paket-Namespace|Der Namespace für die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Paket für diese DSL generiert.|\<keine >|
|Produktname|Der Name des Produkts, das für die zu registrierende der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Paket für diese DSL generiert.|\<keine >|
|Hinweise|Anmerkungen im Zusammenhang mit dieser Domänenklasse.|\<keine >|
|Beschreibung|Beschreibung für diese Domänenklasse.|\<keine >|
|Anzeigename|Der Name, der in der generierten Designer für diese Domänenklasse angezeigt wird.|\<keine >|
|Hilfsschlüsselwort|Das Hilfeschlüsselwort dieser Domänenklasse zugeordnet.|\<keine >|
|Build|Die Anzahl der inkrementellen Build für diese Definition einer domänenspezifischen Sprache.|0|
|Hauptversion|Die inkrementelle Hauptbuildnummer für diese Definition einer domänenspezifischen Sprache.|1|
|Nebenversion|Die Anzahl der inkrementellen Nebenversionsnummer des Builds für diese Definition einer domänenspezifischen Sprache.|0|
|Revision|Die inkrementelle Revision Buildnummer für diese Definition einer domänenspezifischen Sprache.|0|

## <a name="see-also"></a>Siehe auch

- [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)