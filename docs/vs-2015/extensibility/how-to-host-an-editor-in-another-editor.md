---
title: 'Vorgehensweise: Hosten Sie einen Editor in einem anderen Editor | Microsoft-Dokumentation'
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
ms.openlocfilehash: 38e47e918683d375f6a6baded2bf946a60020e64
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958330"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Vorgehensweise: Hosten Sie einen Editor in einem anderen Editor
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
