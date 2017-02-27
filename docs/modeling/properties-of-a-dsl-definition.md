---
title: "Eigenschaften einer DSL-Definition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Definitionsdatei"
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 13
---
# Eigenschaften einer DSL-Definition
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definieren DslDefinitions\-Eigenschaften *domänenspezifische Sprachen* wie Eigenschaften für Versionsnummer.  Die DslDefinitions\-Eigenschaften werden im Fenster **Eigenschaften** , wenn Sie an einem geöffneten Feld des Diagramms im *domänenspezifischen Sprachdesigner*klicken.  
  
 Weitere Informationen finden Sie unter [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md).  Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)verwendet.  
  
 DslDefinition Eigenschaft besitzt die in der folgenden Tabelle:  
  
|Property|Beschreibung|Standardwert|  
|--------------|------------------|------------------|  
|Zugriffsmodifizierer|Bestimmt, ob der Zugriffsmodifizierer für die Domänenklasse intern oder öffentlich ist.|public|  
|Benutzerdefinierte Attribute|definierten benutzerdefinierten Attributen für die Domänenklasse.<br /><br /> **Hinweis** verwenden Sie die Schaltfläche Durchsuchen, um ein Attribut hinzuzufügen.|\<Keine\>|  
|Unternehmensname|Der Name des aktuellen Firmennamens in der Systemregistrierung.|Aktueller Firmenname|  
|Name|Der Name dieser Domänenklasse.|Aktueller Name|  
|Namespace|Der Namespace mit dieser Domänenklasse.|Aktueller Namespace|  
|Paket\-Guid|Die GUID für das Paket [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert für dieses DSL.|\<Keine\>|  
|Paket\-Namespace|Der Namespace für das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Paket generiert für dieses DSL.|\<Keine\>|  
|Produktname|Der Name des Produkts, das zum [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Paket registriert wurde, generierte für dieses DSL.|\<Keine\>|  
|Hinweise|Domänenklasse dieser zugeordneten Hinweise.|\<Keine\>|  
|Beschreibung|Beschreibung für diese Domänenklasse.|\<Keine\>|  
|Angezeigter Name|Der Name, der im generierten Designer für diese Domänenklasse angezeigt wird.|\<Keine\>|  
|Hilfeschlüsselwort|Das Hilfeschlüsselwort Domänenklasse dieser zugeordnet ist.|\<Keine\>|  
|Build|Die inkrementelle Buildnummer für diese Definition domänenspezifische Sprachen.|0|  
|Hauptversion|Die inkrementelle zentrale Buildnummer für diese Definition domänenspezifische Sprachen.|1|  
|Nebenversion|Die inkrementelle kleine Buildnummer für diese Definition domänenspezifische Sprachen.|0|  
|Revision|Die inkrementelle Revisions buildnummer Definition für diese domänenspezifische Sprachen.|0|  
  
## Siehe auch  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)