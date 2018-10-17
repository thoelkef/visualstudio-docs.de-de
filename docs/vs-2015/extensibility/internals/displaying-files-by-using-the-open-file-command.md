---
title: Anzeigen von Dateien mit dem Befehl Open File | Microsoft-Dokumentation
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
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5d9b4198a2d88d7a3a71f07a393ed8e4e07df1e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177540"
---
# <a name="displaying-files-by-using-the-open-file-command"></a>Anzeigen von Dateien mit dem Befehl „Datei öffnen“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die folgenden Schritte beschreiben, wie verarbeitet die IDE die **geöffnete Datei** Befehl, der verfügbar ist. die **Datei** im Menü [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Die Schritte beschreiben außerdem, wie Projekte auf Aufrufe, die von diesem Befehl stammen, reagieren soll.  
  
 Klickt ein Benutzer die **geöffnete Datei** Befehl die **Datei** im Menü und wählt aus einer Datei aus der **geöffnete Datei** im Dialogfeld der folgende Prozess durchgeführt.  
  
1.  Mithilfe der ausgeführten Dokumententabelle, bestimmt die IDE an, ob die Datei bereits in einem Projekt geöffnet ist.  
  
    -   Wenn die Datei geöffnet ist, auftritt die IDE das Fenster an.  
  
    -   Wenn die Datei nicht geöffnet ist, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Abfragen jedes Projekt, um zu bestimmen, welches Projekt die Datei öffnen kann.  
  
        > [!NOTE]
        >  In der Projekt-Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, geben Sie einen Prioritätswert, der die Stufe gibt an, an dem das Projekt die Datei geöffnet. Priority-Werte finden Sie in der <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumeration.  
  
2.  Jedes Projekt gibt eine Prioritätsstufe, die die Wichtigkeit gibt an, es wird auf das Projekt die Datei geöffnet wird.  
  
3.  Die IDE verwendet die folgenden Kriterien, um zu bestimmen, welches Projekt die Datei geöffnet wird:  
  
    -   Das Projekt, das mit der höchsten Priorität (DP_Intrinsic) ist die Datei geöffnet. Wenn mehr als ein Projekt mit dieser Priorität antwortet, wird das erste Projekt, reagieren die Datei geöffnet.  
  
    -   Wenn kein Projekt antwortet mit der höchsten Priorität (DP_Intrinsic), aber alle Projekte reagieren, mit der gleichen, niedriger Priorität, wird das aktive Projekt die Datei geöffnet. Wenn kein Projekt aktiv ist, wird das erste Projekt, reagieren die Datei geöffnet.  
  
    -   Wenn kein Projekt den Besitz der Datei (DP_Unsupported) vorgibt, wird das Projekt verschiedene Dateien die Datei geöffnet.  
  
         Wenn eine Instanz des Projekts sonstige Dateien erstellt wird, reagiert das Projekt immer mit dem Wert DP_CanAddAsExternal. Dieser Wert gibt an, dass das Projekt die Datei öffnen kann. Dieses Projekt werden geöffnete Dateien enthalten, die nicht in anderen Projekten enthalten sind. Die Liste der Elemente in diesem Projekt wird nicht beibehalten; Dieses Projekt werden in **Projektmappen-Explorer** nur wenn er verwendet wird, eine Datei zu öffnen.  
  
         Wenn das Projekt verschiedene Dateien nicht angegeben ist, dass die Datei geöffnet werden können, wurde eine Instanz des Projekts nicht erstellt. In diesem Fall wird die IDE erstellt eine Instanz des Projekts sonstige Dateien, und teilt dem Projekt die Datei geöffnet.  
  
4.  Sobald die IDE stellt fest, welches Projekt die Datei geöffnet wird, ruft der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode für das Projekt.  
  
5.  Das Projekt enthält dann die Möglichkeit, die Datei über einen projektspezifischen Editor oder einem standard-Editor zu öffnen. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md) und [Vorgehensweise: Open-Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)bzw.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von Dateien mit Öffnen mit (Befehl)](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Sie öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Vorgehensweise: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)   
 [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)

