---
title: Erstellen einer Erweiterung mit einem Toolfenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94c8335b8d723ef20c04cfffe6b3788d71ecaa4f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118122"
---
# <a name="creating-an-extension-with-a-tool-window"></a>Erstellen einer Erweiterung mit einem Toolfenster
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Verfahren erfahren Sie, wie Sie die VSIX-Projektvorlage verwenden und die **benutzerdefinierten Toolfensters** Elementvorlage, die eine Erweiterung mit einem Toolfenster zu erstellen.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Erstellen eines Toolfensters  
  
1. Erstellen Sie ein VSIX-Projekt mit dem Namen **FirstWindow**. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2. Wenn das Projekt geöffnet wird, fügen Sie eine Elementvorlage der Tool-Fenster mit dem Namen **FirstWindow**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Toolfensters**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Dateinamen des Tool-Fenster an **FirstWindow.cs**.  
  
3. Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen zur experimentellen Instanz finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
4. Wechseln Sie in der experimentellen Instanz zu **anzeigen / Other Windows**.  
  
     Daraufhin sollte ein Menüelement für **FirstWindow**. Klicken Sie darauf.  
  
     Daraufhin sollte ein Toolfenster mit dem Titel **FirstWindow** und einem Spruch Schaltfläche **hier klicken.**
