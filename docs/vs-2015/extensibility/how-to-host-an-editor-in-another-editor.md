---
title: 'Vorgehensweise: Hosten eines Editors in einem anderen Editor | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4b4ff425feb22b5057a8d1a76b7f73b8932d9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204167"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Vorgehensweise: Hosten eines Editors in einem anderen Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie einen Editor innerhalb eines anderen Hosts hosten, indem Sie das Hostingfenster als übergeordnetes Fenster angeben. Legen Sie hierzu die Parameter <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> und <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> für den untergeordneten Fensterrahmen fest.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>So richten Sie den Fensterrahmen ein, um einen Editor zu hosten  
  
1. Markieren Sie einen Editor als gehosteten Editor, indem Sie einen untergeordneten Fensterbereich erstellen.  
  
     In diesem Bereich wird der Text des Editors angezeigt.  
  
2. Erstellen Sie den Host-Editor mithilfe der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> oder- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> Methode.  
  
3. Legen <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> Sie die-Eigenschaft und die-Eigenschaft <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> in der Fensterrahmen Implementierung des gehosteten Editors fest, indem Sie diese Eigenschaften als Parameter an die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> Methode übergeben.  
  
     Wenn Sie diese Parameter abrufen müssen, übergeben Sie diese Eigenschaften an die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode.  
  
4. Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Methode für den enthaltenen Editor auf.  
  
     Der Editor wird im gehosteten Bereich des enthaltenden Editors angezeigt.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Das **Anwendungs-Designer** in der Visual Studio Team Edition for Architects ist ein Beispiel für einen Editor-Fensterrahmen, der einen anderen Editor gehostet. Der **Anwendungs-Designer** hostet andere Designer im rechten Bereich. Ein Designer Panel (oder eine **Eigenschaften** Seite) für jeden der enthaltenen Designer wird dem enthaltenden Fensterrahmen hinzugefügt.
