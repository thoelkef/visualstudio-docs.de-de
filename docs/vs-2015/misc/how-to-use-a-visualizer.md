---
title: 'Gewusst wie: Verwenden einer Schnellansicht | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f981b76d471658fe82e874901ad784a17841891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778374"
---
# <a name="how-to-use-a-visualizer"></a>Gewusst wie: Verwenden einer Schnellansicht
Sie können den Inhalt einer Variable oder eines Objekts mithilfe einer Schnellansicht in einer für den Datentyp sinnvollen Art anzeigen. Sie können Visualisierungen über **DataTips**, ein **Überwachungs** Fenster, das Fenster Auto oder **das Fenster Lokal** verwenden **Locals** .  
  
 Schnellansichten werden in Compact Framework nicht unterstützt.  
  
> [!NOTE]
> In **Store** -apps werden nur die standardmäßigen Text-, HTML-, XML-und JSON-Visualisierungen unterstützt. Benutzerdefinierte (von Benutzern erstellte) Schnellansichten werden nicht unterstützt.  
  
### <a name="to-open-a-visualizer"></a>So öffnen Sie eine Schnellansicht  
  
1. Klicken Sie auf das Lupensymbol, das neben einem Variablennamen in **DataTips**, einem **Überwachungs** Fenster oder im Fenster **Auto, lokal**oder **schnell Überwachung** angezeigt wird. **Locals**  
  
     Eine Liste von Schnellansichten wird angezeigt.  
  
2. Klicken Sie auf die gewünschte Schnellansicht.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>So verwenden Sie eine Schnellansicht für verwalteten Code während des Remotedebuggens  
  
- Kopieren Sie die Schnellansicht-DLL auf den Remotecomputer, bevor Sie die Debugsitzung starten.  
  
     Der Pfad zur DLL muss auf dem Remotecomputer und dem lokalen Computer derselbe sein. Dieser Pfad kann einer der folgenden Speicherorte sein:  
  
     *Visual Studio-Installationspfad* `\Common7\Packages\Debugger\Visualizers`  
  
     - oder -  
  
     `My Documents\Visual Studio 2010\Visualizers`*Visual Studio-Version*`\Visualizers`  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von benutzerdefinierten Visualisierungen](../debugger/create-custom-visualizers-of-data.md)   
 [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)   
 [Gewusst wie: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md)   
 [Anzeigen von Datenwerten als Datentipps](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)