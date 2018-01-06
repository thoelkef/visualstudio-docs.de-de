---
title: Erstellen eine Erweiterung mit einem Toolfenster | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e4e01959df5da96018aa8f1d06fce1076e732096
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-extension-with-a-tool-window"></a>Erstellen eine Erweiterung mit einem Toolfenster
In diesem Verfahren erfahren Sie, wie Sie die VSIX-Projektvorlage verwenden und die **benutzerdefinierte Toolfenster** Elementvorlage, um eine Erweiterung mit einem Toolfenster zu erstellen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Erstellen eines Toolfensters  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen **FirstWindow**. Sie finden die VSIX-Projektvorlage in die **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine Elementvorlage für Tool-Fenster mit dem Namen **MyWindow**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierte Toolfenster**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Dateinamen des Tool-Fenster an **MyWindow.cs**.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen über die experimentelle Instanz finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
4.  Wechseln Sie in der experimentellen Instanz zu **Ansicht / Weitere Fenster**.  
  
     Daraufhin sollte ein Menüelement für **MyWindow**. Klicken Sie darauf.  
  
     Daraufhin sollte ein Toolfenster mit dem Titel **MyWindow** und eine Schaltfläche sagen **Click Me!.**