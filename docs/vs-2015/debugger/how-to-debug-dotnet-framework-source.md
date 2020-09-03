---
title: 'Vorgehensweise: Debuggen von .NET Framework Quelle | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49b13b8406dc96e8e7ebe5e79e26c5da02e8a53a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205442"
---
# <a name="how-to-debug-net-framework-source"></a>Gewusst wie: Debuggen einer .NET Framework-Quelle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] enthält neue Funktionen für das [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Debuggen. Um [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] die Quelle zu debuggen, müssen Sie Zugriff auf Debugsymbole für den Code haben. Außerdem müssen Sie das schrittweise Aktivieren der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Quelle aktivieren.  
  
 Sie können [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] im Dialogfeld **Optionen** die schrittweise und das Herunterladen von Symbolen aktivieren. Wenn Sie das Herunterladen von Symbolen aktivieren, können Sie angeben, ob Symbole sofort heruntergeladen werden sollen, oder Sie können die Option für das spätere Herunterladen aktivieren. Wenn Sie die Symbole nicht sofort herunterladen, werden die Symbole heruntergeladen, wenn Sie das nächste Mal einen Debugvorgang Ihrer Anwendung starten. Sie können auch einen manuellen Download über das Fenster **Module** oder das Fenster "Fenster" **aufgerufen** werden.  
  
### <a name="to-enable-net-framework-source-debugging"></a>So aktivieren Sie das Debuggen des .NET Framework-Quellcodes  
  
1. Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2. Klicken Sie im Dialogfeld **Optionen** auf die Kategorie **Debuggen** .  
  
3. Legen Sie im Feld **Allgemein** die Option .NET Framework Quellen Schritt **aktivieren** fest.  
  
    1. Wenn Sie Nur Mein Code aktiviert haben, wird Ihnen in einem Warndialogfeld mitgeteilt, dass Nur mein Code jetzt deaktiviert wird. Klicken Sie auf **OK**.  
  
    2. Wenn Sie keinen Speicherort für den Symbolcache festgelegt haben, teilt Ihnen ein anderes Warndialogfeld mit, dass jetzt ein Standardspeicherort für den Symbolcache festgelegt wird. Klicken Sie auf **OK**.  
  
4. Klicken Sie unter der Kategorie **Debugging** auf **Symbole**.  
  
5. Gehen Sie wie folgt vor, wenn Sie den Speicherort des Symbolverzeichnisses ändern möchten:  
  
    1. Öffnen Sie im Feld auf der linken Seite den Knoten **Debuggen** .  
  
    2. Klicken Sie unter dem Knoten **Debuggen** auf **Symbole**.  
  
    3. Bearbeiten Sie den Speicherort in **Symbol Symbole von Symbol Servern in dieses Verzeichnis,** oder klicken Sie auf **Durchsuchen** , um einen Speicherort auszuwählen.  
  
6. Wenn Sie Symbole sofort herunterladen möchten, klicken Sie auf **Symbole mithilfe der obigen Speicherorte laden**.  
  
     Diese Schaltfläche ist im Entwurfsmodus nicht verfügbar.  
  
     Wenn Sie die Symbole nicht sofort herunterladen, werden die Symbole automatisch heruntergeladen, wenn Sie das nächste Mal einen Debugvorgang Ihres Programms starten.  
  
7. Klicken Sie auf **OK**, um das Dialogfeld **Optionen** zu schließen.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>So laden Sie Frameworksymbole mit dem Fenster "Module"  
  
1. Klicken Sie im Fenster **Module** mit der rechten Maustaste auf ein Modul, für das keine Symbole geladen werden. Sie können feststellen, ob Symbole geladen werden oder nicht, indem Sie sich die Spalte **Symbol Status** ansehen.  
  
2. Zeigen Sie auf **Symbole laden aus** , und klicken Sie auf **Microsoft-Symbol Server** , um Symbole vom öffentlichen Microsoft-Symbol Server oder **Symbol Pfad** zum Laden aus einem Verzeichnis herunterzuladen, in dem Sie zuvor Symbole gespeichert haben.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>So laden Sie Frameworksymbole mit dem Fenster "Aufrufliste"  
  
1. Klicken Sie **im Fenster "** Fenster" mit der rechten Maustaste auf einen Frame, für den Symbole nicht geladen werden. Der Rahmen wird abgeblendet.  
  
2. Zeigen Sie auf **Symbole laden aus** , und klicken Sie auf **Microsoft-Symbol Server** oder **Symbol Pfad**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugging von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
