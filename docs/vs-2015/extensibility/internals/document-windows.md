---
title: Dokumentieren von Windows | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c620de56e3658c3aef33da136930221578b9be4a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512539"
---
# <a name="document-windows"></a>Dokumentfenster
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Dokument Windows](https://docs.microsoft.com/visualstudio/extensibility/internals/document-windows).  
  
In Visual Studio eine *Dokumentfenster* ist ein gerahmter untergeordnete Fenster, das ein Fenster für die Multiple Document Interface (MDI) zugeordnet ist. Dokumentfenster in der Regel für die Anzeige und Änderung von Quellcode oder Text verwendet werden, aber sie können auch andere funktionale Typen hosten. Dokumentfenster:  
  
-   Können in separaten horizontale oder vertikale Registerkartengruppen in der übergeordneten MDI organisiert werden, sodass mehrere Dateien gleichzeitig angezeigt werden können.  
  
-   Können in beliebiger Reihenfolge in der übergeordneten MDI angedockt werden.  
  
-   Kostenlos abgedockt werden können.  
  
-   In der Aktivierreihenfolge auf andere MDI-Fenster sind verknüpft werden.  
  
 Die Befehle für die Gruppierung, können auf der rechten Maustaste auf eine Fensterregisterkarte Dokument andockbare und unverankerte gefunden werden.  
  
 Weitere Informationen zu Verhalten in Visual Studio, finden Sie unter [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
## <a name="document-window-implementation"></a>Dokumentfensterimplementierung  
 Dokumentfenster werden erstellt, durch die Implementierung eines Editors. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> -Schnittstelle erstellt Dokumentfenster im Rahmen der Instanziierung eines Editors. Weitere Informationen finden Sie unter [Legacy-Schnittstellen in den Editor](../../extensibility/legacy-interfaces-in-the-editor.md).  
  
> [!NOTE]
>  Rückwärts und navigationspunkte in einem Fenster weiterzuleiten, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> Schnittstelle. Text-Editor wird Textmarkierungen navigationspunkte im Dokument identifiziert.  
  
## <a name="the-running-document-table"></a>Die aktive Dokumenttabelle  
 Die IDE verwendet der ausgeführten Dokumententabelle (RDT), um den Status jedes Dokumentfenster nachzuverfolgen. Der RDT ist der Mechanismus, über welches, den Dokument Windows benachrichtigt werden, Ereignisse, z. B. wenn eine Projektmappe geschlossen wird oder wenn eine Datei bearbeitet wurde. Weitere Informationen finden Sie unter [Running Document Table](../../extensibility/internals/running-document-table.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verzögertes Laden von Dokumenten](../../extensibility/internals/delayed-document-loading.md)

