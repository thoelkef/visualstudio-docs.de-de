---
title: 'Vorgehensweise: Debuggen einer .NET Framework-Quelle | Microsoft-Dokumentation'
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
ms.openlocfilehash: c06a2328987201198bc2d5d15a4788d2a821d7b6
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219119"
---
# <a name="how-to-debug-net-framework-source"></a>Gewusst wie: Debuggen einer .NET Framework-Quelle
Zum Debuggen von .NET Framework-Quellcodes benötigen Sie Zugriff auf Debugsymbole für den Code. Sie müssen auch .NET Framework-Quellcodes-Quellcodes aktivieren.  
  
 Sie können .NET Framework schrittweise ausführen und das Symbol im Download der **Optionen** im Dialogfeld. Wenn Sie das Herunterladen von Symbolen aktivieren, können Sie angeben, ob Symbole sofort heruntergeladen werden sollen, oder Sie können die Option für das spätere Herunterladen aktivieren. Wenn Sie die Symbole nicht sofort herunterladen, werden die Symbole heruntergeladen, wenn Sie das nächste Mal einen Debugvorgang Ihrer Anwendung starten. Auch möglich, einen manuellen Download über die **Module** Fenster oder der **Aufrufliste** Fenster.  
  
### <a name="to-enable-net-framework-source-debugging"></a>So aktivieren Sie das Debuggen des .NET Framework-Quellcodes  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** Dialogfeld klicken Sie auf die **Debuggen** Kategorie.  
  
3.  In der **allgemeine** legen **aktivieren Sie .NET Framework-Quelle schrittweise ausführen.**  
  
    1.  Wenn Sie Nur Mein Code aktiviert haben, wird Ihnen in einem Warndialogfeld mitgeteilt, dass Nur mein Code jetzt deaktiviert wird. Klicken Sie auf **OK**.  
  
    2.  Wenn Sie keinen Speicherort für den Symbolcache festgelegt haben, teilt Ihnen ein anderes Warndialogfeld mit, dass jetzt ein Standardspeicherort für den Symbolcache festgelegt wird. Klicken Sie auf **OK**.  
  
4.  Unter den **Debuggen** (Kategorie), klicken Sie auf **Symbole**.  
  
5.  Wenn Sie den Cachespeicherort Symbole ändern möchten, bearbeiten Sie den Speicherort in **Symbole in diesem Verzeichnis zwischenspeichern** oder klicken Sie auf **Durchsuchen** , einen Standort auszuwählen.  
  
6.  Wenn Sie Symbole sofort herunterladen möchten, klicken Sie auf **Symbole laden von oben angegebenen Speicherorten**.  
  
     Diese Schaltfläche ist im Entwurfsmodus nicht verfügbar, aber während des Debuggens verfügbar ist.  
  
     Wenn Sie die Symbole nicht sofort herunterladen, werden die Symbole automatisch heruntergeladen, wenn Sie das nächste Mal einen Debugvorgang Ihres Programms starten.  
  
7.  Klicken Sie auf **OK**, um das Dialogfeld **Optionen** zu schließen.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>So laden Sie Frameworksymbole mit dem Fenster "Module"  
  
1.  In der **Module** Fenster (Wählen Sie während des Debuggens **Debuggen** > **Windows** > **Module**), mit der rechten Maustaste in ein Modul, das für den keine Symbole geladen sind. Sie können feststellen, ob Symbole geladen sind oder nicht anhand der **Symbolstatus** Spalte.  
  
2.  Zeigen Sie auf **Symboleinstellungen** , und klicken Sie auf **Microsoft-Symbolserver** um Symbole von den öffentlichen Symbolserver Microsoft herunterzuladen. Oder Sie können mit der rechten Maustaste in des Moduls, und wählen Sie **Symbole laden** aus einem Verzeichnis geladen, in dem Sie zuvor Symbole gespeichert haben.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>So laden Sie Frameworksymbole mit dem Fenster "Aufrufliste"  
  
1.  In der **Aufrufliste** Fenster mit der rechten Maustaste einen Rahmen, die für den keine Symbole geladen sind. Der Rahmen wird abgeblendet.  
  
2.  Zeigen Sie auf **Symboleinstellungen** , und klicken Sie auf **Microsoft-Symbolserver**, oder mit der rechten Maustaste in des Moduls, und wählen Sie **Symbolpfad**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)