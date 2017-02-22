---
title: "Hierarchien in Visual Studio | Microsoft Docs"
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
  - "Visual Studio-IDE-Hierarchien"
  - "Hierarchien-IDE"
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Hierarchien in Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung \(IDE\) zeigt ein Projekt als *Hierarchie an*.  In der IDE ist eine Hierarchie eine Struktur von Knoten, in der jeder Knoten einen Satz zugeordneter Eigenschaften verfügt.  Eine *Projekthierarchie* ist ein Container, der die Elemente des Projekts die Beziehungen der Elemente und zugeordneten Eigenschaften und die Befehle Elemente enthält.  
  
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hierarchien Projekt verwalten, indem Sie die Hierarchien Oberfläche, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>verwenden.  Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>\-Schnittstelle wird von Befehlen, die Sie von den Projektelementen auf das entsprechende Fenster Hierarchie Befehls anstelle des standardmäßigen handlers aufrufen.  
  
## Projekt\-Hierarchien  
 Jede Projekthierarchie enthält Elemente, die Sie anzeigen und bearbeiten können.  Diese Elemente unterscheiden sich je nach Projekttyp.  Zum Beispiel könnte ein Datenbankprojekt gespeicherte Prozeduren, Datenbankansichten und Datenbanktabellen.  Ein Datenbankprojekt enthält hingegen Programmiersprachen sich Quelldateien und Ressourcendateien für Bitmap und Dialogfelder.  Hierarchien können geschachtelt werden, sodass Sie einige weitere gibt eine größere Flexibilität beim Erstellen einer Projekthierarchie erstellt werden.  
  
 Wenn Sie ein neuer Projekttyp erstellen, steuert der Projekttyp den vollständigen Satz von Elementen, die dort bearbeitet werden können.  Projekte können jedoch Elemente enthalten, für die sie keine Unterstützung für das Bearbeiten.  Visual C\+\+\-Projekten können z. B. HTML\-Dateien enthalten, obwohl Visual C\+\+ keinen benutzerdefinierten Editor für den HTML\-Datei\-Typ bereitstellt.  
  
 Hierarchien verwalten die Dauerhaftigkeit von Elementen, die sie enthalten.  Die Implementierung der Hierarchie muss alle speziellen Eigenschaften steuern, die die Beibehaltung der Elemente in der Hierarchie auswirken.  Wenn beispielsweise die übergeordnete Objekte in einem Repository anstelle von Dateien darstellen, muss die Implementierung der Hierarchie die Beibehaltung dieser Objekte steuern.  Die IDE selbst verweist auf die Hierarchie, um Elemente der gemäß Benutzereingaben zu speichern, aber keine steuert die IDE, um Aktionen, die zum Speichern dieser Elemente erforderlich sind.  Stattdessen wird das Projekt im Steuerelement.  
  
 Wenn ein Benutzer ein Element in einem Editor geöffnet wird, wird die Hierarchie, die dieses Element ausgewählt und steuert, wird die aktive Hierarchie.  Die ausgewählte Hierarchie bestimmt den Satz von Befehlen, die Sie nach dem Element zu behandeln.  Nachverfolgen Fokus Benutzer können auf diese Weise die Hierarchie, um den aktuellen Kontext des Benutzers zu entsprechen.  
  
## Siehe auch  
 [Projekttypen](../../extensibility/internals/project-types.md)   
 [Auswahl und Währung, in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [VSSDK\-Beispiele](../../misc/vssdk-samples.md)