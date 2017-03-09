---
title: "Gewusst wie: Verwenden einer Schnellansicht | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.dataviewer"
  - "vs.debug.stringviewer"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, Schnellansichten"
  - "Schnellansichten, Informationen über Schnellansichten"
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
caps.handback.revision: 37
ms.author: "susanno"
manager: "douge"
---
# Gewusst wie: Verwenden einer Schnellansicht
Sie können den Inhalt einer Variable oder eines Objekts mithilfe einer Schnellansicht in einer für den Datentyp sinnvollen Art anzeigen.  Sie können Schnellansichten über **DataTips**, ein **Überwachungselement**\-Fenster, das Fenster **Autos** oder das Fenster **Lokal** verwenden.  
  
 Schnellansichten werden in Compact Framework nicht unterstützt.  
  
> [!NOTE]
>  In **Speicher**\-Anwendungen werden nur die Schnellansichten Standardtext, HTML, XML und JSON unterstützt.  Benutzerdefinierte \(von Benutzern erstellte\) Schnellansichten werden nicht unterstützt.  
  
### So öffnen Sie eine Schnellansicht  
  
1.  Klicken Sie in einem **Überwachungsfenster**, im Fenster **Auto**, im Fenster **Lokal** oder im Fenster **Schnellüberwachung** in **DataTips** auf das Lupensymbol neben einem Variablennamen.  
  
     Eine Liste von Schnellansichten wird angezeigt.  
  
2.  Klicken Sie auf die gewünschte Schnellansicht.  
  
### So verwenden Sie eine Schnellansicht für verwalteten Code während des Remotedebuggens  
  
-   Kopieren Sie die Schnellansicht\-DLL auf den Remotecomputer, bevor Sie die Debugsitzung starten.  
  
     Der Pfad zur DLL muss auf dem Remotecomputer und dem lokalen Computer derselbe sein.  Dieser Pfad kann einer der folgenden Speicherorte sein:  
  
     *Visual Studio\-Installationspfad*`\Common7\Packages\Debugger\Visualizers`  
  
     \- oder \-  
  
     `My Documents\Visual Studio 2010\Visualizers`*Visual Studio\-Version*`\Visualizers`  
  
## Siehe auch  
 [Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
 [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)   
 [Gewusst wie: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md)   
 [Anzeigen von Datenwerten als Datentipps](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)