---
title: 'Vorgehensweise: Debuggen von .NET Framework-Quellcodes | Microsoft Docs'
ms.custom: ''
ms.date: 02/23/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8377ed73479441272b2f1910767fa7e2a4ff0196
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-net-framework-source"></a>Gewusst wie: Debuggen einer .NET Framework-Quelle
Um .NET Framework-Quellcode zu debuggen, müssen Sie Zugriff auf Debugsymbole für den Code haben. Sie müssen auch die schrittweise Ausführung von .NET Framework-Quellcodes aktivieren.  
  
 Sie können .NET Framework-Symbol im herunterladen und schrittweise die **Optionen** (Dialogfeld). Wenn Sie das Herunterladen von Symbolen aktivieren, können Sie angeben, ob Symbole sofort heruntergeladen werden sollen, oder Sie können die Option für das spätere Herunterladen aktivieren. Wenn Sie die Symbole nicht sofort herunterladen, werden die Symbole heruntergeladen, wenn Sie das nächste Mal einen Debugvorgang Ihrer Anwendung starten. Sie müssen auch ein manuelles Herunterladen von der **Module** Fenster oder die **Aufrufliste** Fenster.  
  
### <a name="to-enable-net-framework-source-debugging"></a>So aktivieren Sie das Debuggen des .NET Framework-Quellcodes  
  
1.  Auf der **Tools** Menü klicken Sie auf **Option**s.  
  
2.  In der **Optionen** (Dialogfeld), klicken Sie auf die **Debuggen** Kategorie.  
  
3.  In der **allgemeine** legen **Aktivieren von .NET Framework-Quelle schrittweise durchlaufen.**  
  
    1.  Wenn Sie Nur Mein Code aktiviert haben, wird Ihnen in einem Warndialogfeld mitgeteilt, dass Nur mein Code jetzt deaktiviert wird. Klicken Sie auf **OK**.  
  
    2.  Wenn Sie keinen Speicherort für den Symbolcache festgelegt haben, teilt Ihnen ein anderes Warndialogfeld mit, dass jetzt ein Standardspeicherort für den Symbolcache festgelegt wird. Klicken Sie auf **OK**.  
  
4.  Klicken Sie unter der **Debuggen** Kategorie, klicken Sie auf **Symbole**.  
  
5.  Wenn Sie den Cachespeicherort Symbole ändern möchten, bearbeiten Sie den Speicherort in **Symbole in diesem Verzeichnis zwischenspeichern** oder klicken Sie auf **Durchsuchen** um einen Speicherort auszuwählen.  
  
6.  Wenn Sie Symbole sofort herunterladen möchten, klicken Sie auf **Symbole laden von oben angegebenen Speicherorten**.  
  
     Diese Schaltfläche ist im Entwurfsmodus nicht verfügbar, steht jedoch während des Debuggens.  
  
     Wenn Sie die Symbole nicht sofort herunterladen, werden die Symbole automatisch heruntergeladen, wenn Sie das nächste Mal einen Debugvorgang Ihres Programms starten.  
  
7.  Klicken Sie auf **OK**, um das Dialogfeld **Optionen** zu schließen.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>So laden Sie Frameworksymbole mit dem Fenster "Module"  
  
1.  In der **Module** Fenster (während des Debuggens, wählen Sie **Debuggen** > **Windows** > **Module**), mit der rechten Maustaste in ein Modul, das für den keine Symbole geladen sind. Sie können feststellen, ob Symbole geladen sind oder nicht durch einen Blick auf die **Symbolstatus** Spalte.  
  
2.  Zeigen Sie auf **Symboleinstellungen** , und klicken Sie auf **Microsoft-Symbolserver** um Symbole von den öffentlichen Microsoft-Symbolservern herunterzuladen. Oder Sie können mit der rechten Maustaste in des Moduls, und wählen Sie **Symbole laden** um aus einem Verzeichnis zu laden, in dem Sie zuvor Symbole gespeichert haben.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>So laden Sie Frameworksymbole mit dem Fenster "Aufrufliste"  
  
1.  In der **Aufrufliste** Fenster, mit der rechten Maustaste einen Rahmen für den keine Symbole geladen sind. Der Rahmen wird abgeblendet.  
  
2.  Zeigen Sie auf **Symboleinstellungen** , und klicken Sie auf **Microsoft-Symbolserver**, oder mit der rechten Maustaste in des Moduls, und wählen Sie **Symbolpfad**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)