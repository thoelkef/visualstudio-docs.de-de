---
title: 'Vorgehensweise: Hosten von einem Editor in einem anderen Editor | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7bdab7eb1949cb2d1113247c1c537c1a43ccf97
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208519"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Vorgehensweise: Hosten von einem Editor in einem anderen Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie ein Editor in einem anderen durch Angeben des hosting-Fensters als ein übergeordnetes Fenster hosten. Zu diesem Zweck legen Sie die Parameter <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> und <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> auf den untergeordneten Fensterrahmen.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Zum Einrichten des Fensterrahmens zum Hosten eines Editors  
  
1.  Legen Sie einen Editor als einen gehosteten-Editor, durch das Erstellen eines untergeordneten Bereich.  
  
     Dieser Bereich befindet, in dem die Anmerkung der Redaktion Text übertragen werden.  
  
2.  Erstellen der hosting-Editor über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> Methode.  
  
3.  Legen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> und <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> Eigenschaften in der Fenster-Frame-Implementierung des gehosteten Editors durch Übergeben dieser Eigenschaften als Parameter für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> -Methode, bzw.  
  
     Wenn Sie diesen Parameter abgerufen werden müssen, übergeben Sie diese Eigenschaften auf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode.  
  
4.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Methode für den eigenständigen Editor.  
  
     Der Editor wird im Bereich "gehosteten" des enthaltenden-Editors angezeigt.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Die **Anwendungs-Designer** in der Visual Studio Team Edition for Architects ist ein Beispiel eines Editor-Fenster-Frames Hosten von einem anderen Editor. Die **Anwendungs-Designer** hostet andere Designer im rechten Bereich. Ein Designer-Bereich (oder **Eigenschaften** Seite) für jede der enthaltene Designer auf den enthaltenden Fensterrahmen hinzugefügt wird.

