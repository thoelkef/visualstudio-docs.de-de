---
title: "Implementieren der Befehl f&#252;r die geschachtelte Projekte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "geschachtelte Projekte, implementieren die befehlsverarbeitung"
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Implementieren der Befehl f&#252;r die geschachtelte Projekte
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die IDE kann Befehle übergeben, die von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> und die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\-Schnittstellen zu geschachtelten Projekten übergebenen Befehle können die Projekte oder Elemente filtern oder überschreiben.  
  
> [!NOTE]
>  Die ONLY\-Befehle, die normalerweise durch das Projekt Elemente gefiltert werden können, behandelt werden.  Befehle wie **Build** und **Deploy** , die von der IDE behandelt werden, können nicht gefiltert werden.  
  
 Die folgenden Schritte beschreiben den Prozess zum Implementieren eines Befehls Klassenbehandlung.  
  
## Arbeitsschritte  
  
#### So implementieren Sie die Klassenbehandlung Befehls  
  
1.  Wenn der Benutzer ein geschachteltes Projekt oder in einem geschachtelten Projekt auswählen:  
  
    1.  Die IDE ruft die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>\-Methode veranschaulicht.  
  
     \- oder \-  
  
    1.  Wenn der Befehl in einem Fenster Hierarchie, z. B. einen Kontextmenübefehl stammt, klicken Sie im Projektmappen\-Explorer das ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>\-Methode auf dem übergeordneten Element des Projekts an.  
  
2.  Das übergeordnete Projekt kann die `QueryStatus`, wie `pguidCmdGroup` und `prgCmds`zu übergebenden Parameter überprüfen, um zu bestimmen, ob das übergeordnete Projekt die Befehle filtern soll.  Wenn das Projekt Elemente zu filtern, Befehle implementiert wird, sollte es fest:  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     Anschließend sollte das übergeordnete Projekt `S_OK`zurückgeben.  
  
     Wenn das Projekt nicht den Befehl Elemente filtert, muss er gerade `S_OK`zurückgeben.  In diesem Fall führt die IDE automatisch den Befehl auf das untergeordnete Projekt weiter.  
  
     Das übergeordnete Projekt muss mit dem Befehl nicht auf das untergeordnete Projekt weiterleiten.  Die IDE führt diese Aufgabe aus.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Die Schachtelung von Projekten](../../extensibility/internals/nesting-projects.md)