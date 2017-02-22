---
title: "Erstellen von Projekttypen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Bedingung für das Erstellen von Projekttypen"
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Erstellen von Projekttypen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Erstellen eines neuen Projekttyps bietet eine Grundlage für das Anpassen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für den Benutzer.  Wenn ein neuer Projekttyp ist nicht für alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Anpassungen erforderlich.  Die folgenden Richtlinien sollten Ihnen helfen, um zu ermitteln, ob ein neuer Projekttyp für das Szenario erforderlich ist.  
  
## Erstellen Sie einen neuen Projekttyps  
 Sie müssen einen Projekttyp erstellen, wenn Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] anpassen möchten, die in einem oder mehreren der folgenden Methoden fungieren:  
  
-   Der Build wird, stellt Konfigurationen und Quellcodeverwaltung bereit.  
  
-   debugunterstützung bieten.  
  
-   Anzeigenprojektelemente in **Projektmappen\-Explorer**.  
  
-   Verwenden Sie das Dialogfeld **Neues Projekt** oder **Projekt öffnen** .  
  
-   UnterstützungsprojektSchachtelung.  
  
## Erweitern Sie einen vorhandenen Projekttypen  
 Sie sollten ein neuer Projekttyp erstellen, der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wie folgt verwenden kann, um das Verhalten eines vorhandenen Projekttyps z. B. zu ändern oder zu erweitern [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] für den Buildprozess Projekte ändern:  
  
-   Arbeiten mit mehreren Dateien als Einheit aus.  
  
-   Zeigen Sie eine einzelne Datei als Hierarchie von Unterelementen angezeigt.  
  
-   Anzeigen eines Befehls Elementkontext um Editoren an.  
  
-   Zeigen Sie einen Dienstkontext für Editoren an.  
  
## Verwenden Sie einen vorhandenen Projekttypen  
 Erstellen eines neuen Projekts ist manchmal nicht notwendig.  In der folgenden Tabelle sind die Aufgaben, die Sie für einen Projekttyp nicht erstellt werden müssen.  
  
|Aufgabe|Beschreibung|  
|-------------|------------------|  
|Befehle für die Behandlung|Jedes VSPackage können Befehle behandeln.|  
|Erstellen eines Editor|Benutzerdefinierte Editoren können registriert werden.  Weitere Informationen finden Sie unter [Document Windows and Editors](http://msdn.microsoft.com/de-de/603625e1-62b6-413a-bc44-089346e166bc).|  
|Fenster besitzen|Sie können Tools und Dokumentfenster erstellen, ohne ein neuer Projekttyp hinzuzufügen.|  
|Eigenschaften im Eigenschaftenfenster verfügbar machen|Alle Objekte können Eigenschaften verfügbar machen.|  
  
## Erstellen Sie einen Projekt\-Untertyp  
 Sie können einen untertypen Projekt mit verwaltetem Projekttyp zu erweitern, ohne ein neuer Projekttyp zu erstellen.  Aggregation der Projekt untertyp\-Verwendung COM, um den verwalteten Projekten erweitern geschrieben in Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  Mit COM\-Aggregation können Sie einen Großteil der Implementierung des verwalteten Projektsystem wiederverwenden und für ein bestimmtes Szenario durch Aggregation und Verwendung von Unterstützung von Schnittstellen weiter anpassen.  Weitere Informationen zu Projekt untertypen, finden Sie unter [Projekt\-Untertypen](../../extensibility/internals/project-subtypes.md).  
  
## Siehe auch  
 [Document Windows and Editors](http://msdn.microsoft.com/de-de/603625e1-62b6-413a-bc44-089346e166bc)   
 [Prüfliste: Erstellen von neuen Typen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)