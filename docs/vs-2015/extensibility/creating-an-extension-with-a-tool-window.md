---
title: Erstellen einer Erweiterung mit einem Tool Fenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431848"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Erstellen einer Erweiterung mit einem Toolfenster
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Verfahren erfahren Sie, wie Sie mithilfe der VSIX-Projektvorlage und der Element Vorlage für **benutzerdefinierte Tool Fenster** eine Erweiterung mit einem Tool Fenster erstellen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Erstellen eines Tool Fensters  
  
1. Erstellen Sie ein VSIX-Projekt mit dem Namen **firstwindow**. Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** " unter **Visual c#/Erweiterbarkeit**.  
  
2. Wenn das Projekt geöffnet wird, fügen Sie eine Tool Fenster-Element Vorlage mit dem Namen **firstwindow**hinzu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Hinzufügen/Neues Element**aus. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#/Erweiterbarkeit** , und wählen Sie **benutzerdefiniertes Tool Fenster**aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Dateinamen des Tool Fensters in **FirstWindow.cs**.  
  
3. Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen über die experimentelle Instanz finden Sie in [der experimentellen Instanz](../extensibility/the-experimental-instance.md).  
  
4. Wechseln Sie in der experimentellen Instanz zu Ansicht > **andere Fenster**.  
  
     Ein Menü Element für " **firstwindow**" sollte angezeigt werden. Klicken Sie auf diese Schaltfläche.  
  
     Es sollte ein Tool Fenster mit dem Titel **firstwindow** und eine Schaltfläche mit dem Namen **Click me!** angezeigt werden.
