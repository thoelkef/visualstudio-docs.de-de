---
title: "Dokumentfenster | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK Dokumentfenster"
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Dokumentfenster
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In Visual Studio eine *Dokumentfenster* ist eine begrenzte untergeordnetes Fenster, das einem Fenster Multiple Document Interface \(MDI\) zugeordnet ist. Dokumentfenster werden normalerweise für die Anzeige und die Änderung des Quellcodes oder Text verwendet, aber sie können auch andere funktionale Typen hosten. Dokumentfenster:  
  
-   Können separate horizontalen oder vertikalen Registerkartengruppen im übergeordneten MDI verwaltet werden, damit mehrere Dateien gleichzeitig angezeigt werden können.  
  
-   Können in beliebiger Reihenfolge in der übergeordneten MDI angedockt werden.  
  
-   Frei abgedockt werden können.  
  
-   In der Aktivierreihenfolge für andere MDI\-Fenster verknüpft sind.  
  
 Die Befehle für die Gruppierung, können auf das Kontextmenü für ein Fenster Dokumentregisterkarte andockbare und unverankerte gefunden werden.  
  
 Weitere Informationen zum Verhalten in Visual Studio finden Sie unter [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## Dokumentfensterimplementierung  
 Dokumentfenster werden erstellt, durch die Implementierung eines Editors. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> \-Schnittstelle erstellt Dokumentfenster als Teil der Instanziierung eines Editors. Weitere Informationen finden Sie unter [Legacy\-Schnittstellen im Editor](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Implementieren Sie rückwärts und Vorwärts Points für die Navigation in einem Fenster, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> Schnittstelle. Der Text\-Editor wird Text Marker Points für die Navigation im Dokument identifiziert.  
  
## Document\-Tabelle ausgeführt wird  
 Die IDE verwendet die ausgeführten Dokumenttabelle \(RDT\), um den Status jedes Dokumentfenster nachzuverfolgen. Die RDT ist der Mechanismus, durch welche, den Dokument Windows benachrichtigt werden, Ereignisse, z. B. wenn eine Projektmappe geschlossen wird oder wenn eine Datei bearbeitet wurde. Weitere Informationen finden Sie unter [Dokumenttabelle der ausgeführten](../../extensibility/internals/running-document-table.md).  
  
## Siehe auch  
 [Verzögertes Laden von Dokument](../../extensibility/internals/delayed-document-loading.md)