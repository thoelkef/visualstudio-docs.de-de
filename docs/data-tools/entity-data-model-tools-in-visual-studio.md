---
title: "ADO.NET Entity Data Model-Tools | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 21
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ADO.NET Entity Data Model-Tools
Die [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]\-Tools wurden entworfen, um Sie beim Erstellen von [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]\-Anwendungen zu unterstützen.  Die vollständige Dokumentation für die [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]\-Tools finden Sie hier: [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/de-de/91076853-0881-421b-837a-f582f36be527).  
  
 Mit den [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]\-Tools können Sie ein *konzeptionelles Modell* aus einer vorhandenen Datenbank erstellen und das Modell anschließend grafisch darstellen und bearbeiten.  Außerdem können Sie zuerst grafisch ein konzeptionelles Modell erstellen, und anschließend eine Datenbank generieren, die dieses Modell unterstützt.  In beiden Fällen können Sie das Modell automatisch aktualisieren, wenn Änderungen an der zugrunde liegenden Datenbank vorgenommen werden, und Sie können automatisch Code auf Objektebene für die Anwendung generieren.  Die Datenbankgenerierung und die Codegenerierung auf Objektebene können vom Benutzer angepasst werden.  
  
 In der folgenden Liste werden die verschiedenen Entity Data Model\-Tools erläutert:  
  
-   Mit dem [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]\-Designer \(Entity Designer\) können Sie visuell Entitäten, Zuordnungen und Vererbungsbeziehungen erstellen und bearbeiten.  Der Entity Designer generiert außerdem [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)]\- oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Code auf Objektebene.  
  
-   Mit dem [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]\-Assistenten können Sie ein konzeptionelles Modell einer vorhandenen Datenbank generieren und Ihrer Anwendung Datenbankverbindungsinformationen hinzufügen.  
  
-   Mit dem Assistenten zur Datenbankenerstellung können Sie zuerst ein konzeptionelles Modell und im Anschluss daran eine Datenbank erstellen, die dieses Modell unterstützt.  
  
-   Mit dem Modellaktualisierungs\-Assistenten können Sie das konzeptionelle Modell, das Speichermodell und die Zuordnungen aktualisieren, wenn Änderungen an der zugrunde liegenden Datenbank vorgenommen wurden.  
  
    > [!NOTE]
    >  Ab Visual Studio 2010 bieten die [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]\-Tools keine Unterstützung mehr für [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].  
  
 Die Tools generieren oder ändern die Informationen in einer EDMX\-Datei, die das konzeptionelle Modell, das Speichermodell und die Zuordnungen zwischen ihnen beschreiben.  Weitere Informationen finden Sie unter [.edmx File Overview](http://msdn.microsoft.com/de-de/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
 Es gibt auch ein Befehlszeilentool, das entworfen wird, um Anwendungen zu erstellen, die das EDM verwenden: das EdmGen.exe\-Tool.  Dieses Tool kann ein konzeptionelles Modell generieren, ein vorhandenes Modell überprüfen, Quellcodedateien mit Objektklassen erzeugen, die auf dem konzeptionellen Modell basieren, sowie Quellcodedateien erzeugen, die vom Modell generierte Ansichten enthalten.  Ausführliche Informationen zur Verwendung dieses Befehlszeilentools finden Sie unter [EDM\-Generator \(EdmGen.exe\)](../Topic/EDM%20Generator%20\(EdmGen.exe\).md).  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[ADO.NET Entity Framework](../Topic/ADO.NET%20Entity%20Framework.md)|Beschreibt die Verwendung der [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]\-Tools, die von [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] zum Erstellen von Anwendungen bereitgestellt werden.|  
|[Entity Data Model](../Topic/Entity%20Data%20Model.md)|Stellt Links und Informationen über die Verarbeitung von Daten bereit, die von Anwendungen verwendet werden, die auf [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] basieren.|