---
title: Anzeigen von Dateien mit dem Befehl Open File | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f2cbcb6e6239552ae32c817601634587a2fe3a41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="displaying-files-by-using-the-open-file-command"></a>Anzeigen von Dateien mit dem Befehl Open File
Die folgenden Schritte beschreiben, wie die IDE behandelt die **Dateiöffnungsmodus** Befehl, der verfügbar ist die **Datei** im Menü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Die Schritte werden auch beschrieben, wie Projekte auf Aufrufe reagieren soll, die von diesem Befehl stammen.  
  
 Wenn ein Benutzer klickt der **geöffnete Datei** Befehl der **Datei** im Menü und wählt aus einer Datei aus der **geöffnete Datei** (Dialogfeld), der folgende Prozess tritt.  
  
1.  Mithilfe der Dokumenttabelle der ausgeführten, bestimmt die IDE an, ob die Datei bereits in einem Projekt geöffnet ist.  
  
    -   Wenn die Datei geöffnet ist, auftritt die IDE das Fenster an.  
  
    -   Wenn die Datei nicht geöffnet ist, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Abfragen jedes Projekt, um zu bestimmen, welches Projekt die Datei öffnen kann.  
  
        > [!NOTE]
        >  In der Projekt-Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, geben Sie einen Priority-Wert, der die Ebene angibt, an dem das Projekt die Datei geöffnet. Priority-Werte finden Sie in der <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumeration.  
  
2.  Jedes Projekt mit einer Prioritätsebene, die die Wichtigkeit gibt an, antwortet er platziert, auf das Projekt die Datei geöffnet wird.  
  
3.  Die IDE verwendet die folgenden Kriterien, um zu bestimmen, welches Projekt die Datei geöffnet wird:  
  
    -   Das Projekt, das mit der höchsten Priorität (DP_Intrinsic) reagiert, wird die Datei geöffnet. Wenn mehr als ein Projekt mit der Priorität antwortet, wird das erste Projekt reagieren die Datei geöffnet.  
  
    -   Wenn kein Projekt antwortet mit der höchsten Priorität (DP_Intrinsic), aber alle Projekte-Antwort mit der gleichen, niedrigere Priorität, wird das aktive Projekt die Datei geöffnet. Wenn kein Projekt aktiv ist, wird das erste Projekt reagieren die Datei geöffnet.  
  
    -   Wenn kein Projekt den Besitz der Datei (DP_Unsupported) vorgibt, wird das Projekt verschiedene Dateien die Datei geöffnet.  
  
         Wenn eine Instanz des Projekts sonstige Dateien erstellt wird, antwortet das Projekt immer mit dem Wert DP_CanAddAsExternal. Dieser Wert gibt an, dass das Projekt die Datei öffnen kann. Dieses Projekt wird verwendet, um geöffnete Dateien gespeichert, die nicht in anderen Projekten sind. Die Liste der Elemente in diesem Projekt wird nicht beibehalten; Dieses Projekt ist sichtbar, in **Projektmappen-Explorer** nur wenn er verwendet wird, eine Datei zu öffnen.  
  
         Wenn das Projekt verschiedene Dateien nicht angegeben ist, dass die Datei geöffnet werden kann, wurde eine Instanz des Projekts nicht erstellt. In diesem Fall wird die IDE erstellt eine Instanz des Projekts verschiedene Dateien und weist das Projekt zum Öffnen der Datei.  
  
4.  Sobald die IDE stellt fest, welches Projekt die Datei geöffnet wird, ruft der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode auf dieses Projekt.  
  
5.  Das Projekt hat die Möglichkeit, die Datei mit einem projektspezifischen oder standard-Editor zu öffnen. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen projektspezifische Editoren](../../extensibility/how-to-open-project-specific-editors.md) und [wie: Standard-öffnen-Editoren](../../extensibility/how-to-open-standard-editors.md)bzw..  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen von Dateien mit Öffnen mit (Befehl)](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Vorgehensweise: Öffnen von Editoren projektspezifische](../../extensibility/how-to-open-project-specific-editors.md)   
 [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)