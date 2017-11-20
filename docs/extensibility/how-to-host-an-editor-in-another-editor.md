---
title: 'Vorgehensweise: Hosten einen-Editor in einem anderen Editor | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 26819cccc4f5359da83684575423f8d0be276497
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Vorgehensweise: Hosten einen-Editor in einem anderen Editor
In Visual Studio können Sie einen Editor in einem anderen durch Angabe der hosting-Fensters als ein übergeordnetes Fenster hosten. Zu diesem Zweck legen Sie die Parameter <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> und <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> auf den untergeordneten Fenster Frame.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Zum Einrichten der Fensterrahmen zum Hosten eines Editors  
  
1.  Legen Sie einen Editor als gehostete Editor, indem Sie einen untergeordnetes Fenster-Bereich erstellen.  
  
     Dieser Bereich befindet, in dem die EditorText geleitet werden.  
  
2.  Erstellen Sie hosting-Editor mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> Methode.  
  
3.  Festlegen der <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> und <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> Eigenschaften in der Implementierung des Fenster-Frame im gehosteten Editor durch diese Eigenschaften als Parameter übergeben der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> Methode bzw..  
  
     Wenn Sie diesen Parameter abgerufen werden müssen, übergeben Sie diese Eigenschaften auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode.  
  
4.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Methode für den eigenständigen-Editor.  
  
     Der Editor, die in der gehosteten Bereich des enthaltenden-Editors angezeigt werden.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Die **Anwendungsdesigner** in Visual Studio Team Edition for Architects ist ein Beispiel für ein Editor Fensterrahmen, der einen anderen Editor hostet. Die **Anwendungsdesigner** hostet andere Designer im rechten Bereich. Ein Designer-Bereich (oder **Eigenschaften** Seite ") für jede der enthaltene Designer enthaltenden Fensterrahmen hinzugefügt wird.