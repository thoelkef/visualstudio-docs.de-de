---
title: "Gewusst wie: Debuggen einer .NET Framework-Quelle | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen, .NET Framework-Quelle"
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Debuggen einer .NET Framework-Quelle
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die neueste Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] stellt neue Features für das [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Debugging bereit.  Um den [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Quellcode zu debuggen, müssen Sie Zugriff auf Debugsymbole für den Code haben.  Außerdem müssen Sie die schrittweise Ausführung des [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Quellcodes aktivieren.  
  
 Sie können die schrittweise Ausführung von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] und das Herunterladen von Symbolen im Dialogfeld **Optionen** aktivieren.  Wenn Sie das Herunterladen von Symbolen aktivieren, können Sie angeben, ob Symbole sofort heruntergeladen werden sollen, oder Sie können die Option für das spätere Herunterladen aktivieren.  Wenn Sie die Symbole nicht sofort herunterladen, werden die Symbole heruntergeladen, wenn Sie das nächste Mal einen Debugvorgang Ihrer Anwendung starten.  Sie können auch einen manuellen Download über das Fenster **Module**  oder das Fenster**Aufrufliste** ausführen.  
  
### So aktivieren Sie das Debuggen des .NET Framework\-Quellcodes  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Klicken Sie im Dialogfeld **Optionen** auf die Kategorie **Debuggen**.  
  
3.  Legen Sie im Feld **Allgemein** das Durchlaufen des **.NET Framework aktivieren**\-Quellcodes fest.  
  
    1.  Wenn Sie Nur Mein Code aktiviert haben, wird Ihnen in einem Warndialogfeld mitgeteilt, dass Nur mein Code jetzt deaktiviert wird.  Klicken Sie auf **OK**.  
  
    2.  Wenn Sie keinen Speicherort für den Symbolcache festgelegt haben, teilt Ihnen ein anderes Warndialogfeld mit, dass jetzt ein Standardspeicherort für den Symbolcache festgelegt wird.  Klicken Sie auf **OK**.  
  
4.  Klicken Sie unter der Kategorie **Debugging** auf **Symbole**.  
  
5.  Gehen Sie wie folgt vor, wenn Sie den Speicherort des Symbolverzeichnisses ändern möchten:  
  
    1.  Öffnen Sie im Feld links den Knoten **Debugging**.  
  
    2.  Klicken Sie unter dem Knoten **Debugging** auf **Symbole**.  
  
    3.  Bearbeiten Sie den Speicherort in **Symbole vom Symbolserver in diesem Verzeichnis zwischenspeichern**, oder klicken Sie auf **Durchsuchen**, um einen Speicherort auszuwählen.  
  
6.  Wenn Sie Symbole sofort herunterladen möchten, klicken Sie auf **Symbole von oben angegebenen Speicherorten laden**.  
  
     Diese Schaltfläche ist im Entwurfsmodus nicht verfügbar.  
  
     Wenn Sie die Symbole nicht sofort herunterladen, werden die Symbole automatisch heruntergeladen, wenn Sie das nächste Mal einen Debugvorgang Ihres Programms starten.  
  
7.  Klicken Sie auf **OK**, um das Dialogfeld **Optionen** zu schließen.  
  
### So laden Sie Frameworksymbole mit dem Fenster "Module"  
  
1.  Klicken Sie im Fenster **Module** mit der rechten Maustaste auf ein Modul, für das keine Symbole geladen sind.  Sie können in der Spalte **Symbolstatus** feststellen, ob Symbole geladen sind.  
  
2.  Zeigen Sie auf **Symbole laden aus**, und klicken Sie auf **Microsoft\-Symbolserver**, um Symbole von den öffentlichen Microsoft\-Symbolservern herunterzuladen, oder klicken Sie auf **Symbolpfad**, um Symbole aus einem Verzeichnis zu laden, in dem Sie zuvor Symbole gespeichert haben.  
  
### So laden Sie Frameworksymbole mit dem Fenster "Aufrufliste"  
  
1.  Klicken Sie im Fenster **Aufrufliste** mit der rechten Maustaste auf einen Rahmen, für den keine Symbole geladen sind.  Der Rahmen wird abgeblendet.  
  
2.  Zeigen Sie auf **Symbole laden aus**, und klicken Sie auf **Microsoft\-Symbolserver** oder **Symbolpfad**.  
  
## Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)