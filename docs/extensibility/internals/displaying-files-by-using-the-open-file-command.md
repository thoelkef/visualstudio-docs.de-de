---
title: "Anzeigen von Dateien mit dem Befehl Datei &#246;ffnen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekttypen unterstützende Datei öffnen (Befehl)"
  - "Datei öffnen (Befehl)"
  - "Persistenz, unterstützende Datei öffnen (Befehl)"
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Anzeigen von Dateien mit dem Befehl Datei &#246;ffnen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die folgenden Schritte beschreiben, wie die IDE den **Datei öffnen** Befehl behandelt, der auf dem **Datei** Menü in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verfügbar ist.  Die Schritte beschreiben, wie auch für Projekte reagieren sollten Aufrufe von diesem Befehl stammen.  
  
 Wenn ein Benutzer auf den **Datei öffnen** Befehl im Menü **Datei** klicken und eine Datei aus dem **Datei öffnen** Dialogfeld auswählt, tritt der folgende Prozess auf.  
  
1.  Verwenden der Tabelle bestimmt die IDE die Ausführung von Dokumenten, ob die Datei bereits in einem Projekt geöffnet wird.  
  
    -   Beim Öffnen der Datei erneuert die IDE das Fenster.  
  
    -   Wenn die Datei nicht geöffnet ist, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> an, um jedes Projekt abfragen, um zu bestimmen, welches Projekt die Datei öffnen kann.  
  
        > [!NOTE]
        >  In der Projektdurchführung des <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, erstellen Sie den Prioritätswert bereit, der die Ebene angibt, an der das Projekt die Datei geöffnet.  Priorität Attributwerte werden in der <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>\-Enumeration bereitgestellt.  
  
2.  Jedes Projekt antwortet mit einer Prioritätsebene, die die Wichtigkeit angibt, die sich auf, wenn das Projekt eingefügt, die Datei zu öffnen.  
  
3.  Die IDE verwendet die folgenden Kriterien bestimmt, welches Projekt die Datei geöffnet:  
  
    -   Das Projekt, das mit der höchsten Priorität reagiert \(DP\_Intrinsic\) öffnet die Datei.  Wenn mehr als ein Projekt mit dieser Priorität antwortet, wird das erste Projekt die Datei zu reagieren.  
  
    -   Wenn kein Projekt mit der höchsten Priorität \(DP\_Intrinsic\) reagiert, aber alle Projekte mit demselben reagieren, öffnet niedrigere Priorität, das aktive Projekt die Datei.  Wenn kein Projekt aktiv ist, wird das erste Projekt die Datei zu reagieren.  
  
    -   Wenn kein Projekt Besitz der Datei \(DP\_Unsupported\) entspricht, wird das Projekt Verschiedene Dateien.  
  
         Wenn eine Instanz des projekts Verschiedene Dateien erstellt wird, reagiert das Projekt immer mit dem Wert DP\_CanAddAsExternal.  Dieser Wert gibt an, dass dem Projekt die Datei öffnen kann.  Dieses Projekt wird, geöffnete Dateien aufzunehmen, die in keinem anderen Projekt befinden.  Die Liste der Elemente in diesem Projekt wird nicht beibehalten. **Projektmappen\-Explorer** in diesem Projekt ist nur sichtbar, wenn es verwendet wird, um eine Datei zu öffnen.  
  
         Wenn das Projekt Verschiedene Dateien nicht angegeben, dass die Datei öffnen kann, ist eine Instanz des Projekts nicht erstellt wurde.  In diesem Fall erstellt die IDE eine Instanz des projekts Verschiedene Dateien und weist das Projekt, die Datei zu öffnen.  
  
4.  Sobald die IDE bestimmt, welches Projekt die Datei geöffnet wird, ruft es die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>\-Methode für dieses Projekt an.  
  
5.  Standardmäßig weist das Projekt dann die Option des Öffnens der Datei, indem Sie einen projektspezifischen Editor oder einen Standardwert des Editors verwendet.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen von Editoren projektspezifische](../../extensibility/how-to-open-project-specific-editors.md) und [Gewusst wie: Öffnen Sie die Standard\-Editoren](../../extensibility/how-to-open-standard-editors.md).  
  
## Siehe auch  
 [Anzeigen von Dateien mit Öffnen mit \(Befehl\)](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Gewusst wie: Öffnen von Editoren projektspezifische](../../extensibility/how-to-open-project-specific-editors.md)   
 [Gewusst wie: Öffnen Sie die Standard\-Editoren](../../extensibility/how-to-open-standard-editors.md)