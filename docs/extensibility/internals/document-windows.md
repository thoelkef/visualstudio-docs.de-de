---
title: Dokumentieren Sie Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 17
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 03e61b80aaf4c5c8b0e25f5b2a4a42f13d75d305
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="document-windows"></a>Dokumentfenster
In Visual Studio eine *Dokumentfenster* ist eine begrenzte untergeordnetes Fenster, die einem Fenster Multiple Document Interface (MDI) zugeordnet ist. Dokumentfenster in der Regel für die Anzeige und Änderung der Quellcode oder Text verwendet werden, aber sie können auch andere funktionale Typen hosten. Dokumentfenster:  
  
-   Können in separaten horizontale oder vertikale Registerkartengruppen im übergeordneten MDI organisiert werden, damit, dass mehrere Dateien gleichzeitig angezeigt werden können.  
  
-   Können in beliebiger Reihenfolge in der übergeordneten MDI angedockt werden.  
  
-   Kann kostenlos umfließt.  
  
-   In der Aktivierreihenfolge für andere MDI-Fenster verknüpft sind.  
  
 Die Befehle zum Gruppieren auswählen, können auf das Kontextmenü für ein Fenster Dokumentregisterkarte andockbare und unverankerte gefunden werden.  
  
 Weitere Informationen zum Verhalten des Fensters in Visual Studio finden Sie unter [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Implementierung des Dokuments-Fenster  
 Dokumentfenster werden erstellt, durch die Implementierung eines Editors. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> -Schnittstelle erstellt Dokumentfenster im Rahmen der Instanziierung eines Editors. Weitere Informationen finden Sie unter [Legacy-Schnittstellen im Editor](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Rückwärts und Vorwärts Points für die Navigation in einem Fenster, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> Schnittstelle. Der Text-Editor wird Text Marker Points für die Navigation im Dokument identifiziert.  
  
## <a name="the-running-document-table"></a>Document-Tabelle ausgeführt wird  
 Die IDE verwendet die ausgeführten Document-Tabelle (RDT) den Status jedes Dokumentfenster verfolgen. Die RDT ist der Mechanismus, durch welche, den Dokument Windows benachrichtigt werden, der Ereignisse, z. B. wenn eine Projektmappe geschlossen wird oder wenn eine Datei bearbeitet wurde. Weitere Informationen finden Sie unter [Document-Tabelle ausgeführt](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verzögertes Laden von Dokumenten](../../extensibility/internals/delayed-document-loading.md)