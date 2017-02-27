---
title: "Erstellen eine Erweiterung mit einem Toolfenster | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Erstellen eine Erweiterung mit einem Toolfenster
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Verfahren erfahren Sie, wie Sie die VSIX\-Projektvorlage und der **benutzerdefinierte Toolfenster** Elementvorlage beim Erstellen einer Erweiterung mit einem Toolfenster.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
### Erstellen eines Toolfensters  
  
1.  Erstellen Sie ein VSIX\-Projekt namens **FirstWindow**. Sie finden die VSIX\-Projektvorlage in die **Neues Projekt** Dialogfeld unter **Visual c\# \/ Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie eine Elementvorlage der Tool\-Fenster mit dem Namen **FirstWindow**. In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. In der **Neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c\# \/ Erweiterbarkeit** und wählen Sie **benutzerdefinierte Toolfenster**. In den **Namen** Feld am unteren Rand des Fensters, ändern Sie den Dateinamen des Tool\-Fenster an **FirstWindow.cs**.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen über die experimentelle Instanz finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
4.  Wechseln Sie in der experimentellen Instanz zu **Anzeigen \/ andere Fenster**.  
  
     Daraufhin sollte ein Menüelement für **FirstWindow**. Klicken Sie darauf.  
  
     Daraufhin sollte ein Fenster mit dem Titel **FirstWindow** und eine Schaltfläche sagen: **Click Me\!.**