---
title: "MSBuild-Fehler MSB3841 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.ResolveSDKReference.InvalidDependencyInPlatform"
ms.assetid: 80ed22a1-bd62-4ace-892f-6b6009dff8e5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild-Fehler MSB3841
**MSB3841: Das SDK "{1}" hängt vom SDK "{0}" ab, das nicht mit Projekten kompatibel ist, die auf die Plattformversion "{2}" abzielen.**  
  
 MSBuild generiert diesen Fehler, wenn das Projekt über eine Abhängigkeit verfügt, die nicht mit der Plattform kompatibel ist, auf die Ihr Projekt abzielt.  Nicht kompatible Abhängigkeiten verursachen möglicherweise Fehler oder unerwartetes App\-Verhalten zur Laufzeit.  
  
### So korrigieren Sie diesen Fehler für Projektverweise  
  
1.  Visual Basic\-, C\#\-, C\+\+\- und JavaScript\-Projekte, die auf [!INCLUDE[win81](../debugger/includes/win81_md.md)] Store\-Projekte abzielen, dürfen nicht auf C\+\+\-Windows Store\-Projekte für [!INCLUDE[win8](../debugger/includes/win8_md.md)] verweisen, da dies Laufzeitprobleme verursacht.  Falls ein Projekt in Ihrer App auf [!INCLUDE[win81](../debugger/includes/win81_md.md)] abzielt und die App aus einem C\+\+\-Windows Store\-Projekt besteht, müssen Sie folgende Schritte ausführen:  
  
2.  Ändern Sie die Zielversion der Projekte in Ihrer App in [!INCLUDE[win81](../debugger/includes/win81_md.md)].  Klicken Sie dazu auf jedes Projekt in Ihrer App mit der rechten Maustaste, wählen Sie den Befehl **Windows 8.1 neu zuweisen**, und klicken Sie im Dialogfeld **Änderungen an Projekt und Projektmappe überprüfen** auf **OK**.  
  
3.  Klicken Sie mit rechten Maustaste auf jedes Visual Basic\-, C\#\- und JavaScript\-Projekt, das von einem C\+\+\-Windows Store\-Projekt abhängt, wählen Sie **Verweis hinzufügen** aus, rufen Sie die Registerkarte **Windows** und dann die Unterregisterkarte **Erweiterungen** auf, deaktivieren Sie **Microsoft Visual C\+\+ Runtime Package v11.0**, aktivieren Sie **Microsoft Visual C\+\+ Runtime Package v12.0**, und klicken Sie dann auf **OK**.  
  
4.  Visual Basic\-, C\#\- und JavaScript\-Windows Store\-Projekte, die auf [!INCLUDE[win81](../debugger/includes/win81_md.md)] abzielen, können auf Visual Basic\- und C\#\-Windows Store\-Projekte verweisen, die auf [!INCLUDE[win8](../debugger/includes/win8_md.md)] abzielen, sofern die [!INCLUDE[win8](../debugger/includes/win8_md.md)] Store\-Projekte keine APIs verwenden, die in [!INCLUDE[win81](../debugger/includes/win81_md.md)] als veraltet gelten.  Lesen Sie [Migrieren von Windows 8\-Apps zu Windows 8.1 Preview](http://msdn.microsoft.com/library/windows/apps/dn263113.aspx), um zu erfahren, ob die [!INCLUDE[win8](../debugger/includes/win8_md.md)] Store\-Projekte weiter wie erwartet funktionieren, wenn auf sie von einem [!INCLUDE[win81](../debugger/includes/win81_md.md)]\-Projekt verwiesen wird.  
  
     [!INCLUDE[win8](../debugger/includes/win8_md.md)] Store\-Projekte dürfen nicht von Windows Store\-Projekten oder \-Binärdateien abhängen, die auf [!INCLUDE[win81](../debugger/includes/win81_md.md)] abzielen.  
  
### So korrigieren Sie diesen Fehler für Verweise auf Erweiterungs\-SDKs  
  
1.  Visual Basic\-, C\#\-, C\+\+\- und JavaScript\-Windows Store\-Projekte, die auf [!INCLUDE[win81](../debugger/includes/win81_md.md)] abzielen, können nicht auf Erweiterungs\-SDKs verweisen, die von Microsoft Visual C\+\+ Runtime Package v11.0 abhängen, da dies während der Laufzeit auftretende Probleme verursacht.  Sie können ermitteln, ob ein Erweiterungs\-SDK von Microsoft Visual C\+\+ Runtime Package v11.0 abhängt, indem Sie ein neues C\#\-Windows Store\-Projekt erstellen, mit der rechten Maustaste auf das Projekt klicken und **Verweis hinzufügen** auswählen, dann die Registerkarte **Windows** und die Unterregisterkarte **Erweiterungen** aufrufen, das Erweiterungs\-SDK auswählen und prüfen, ob im rechten Bereich des **Verweis\-Managers** die **Microsoft.VCLibs, version \= 11.0** als Abhängigkeit zu finden ist.  
  
     Visual Basic\-, C\#\- und JavaScript\-Windows Store\-Projekte, die auf [!INCLUDE[win81](../debugger/includes/win81_md.md)] abzielen, können auf Erweiterungs\-SDKs verweisen, die nicht von Microsoft Visual C\+\+ Runtime Package v11.0 abhängen, sofern diese Erweiterungs\-SDKs keine APIs verwenden, die in [!INCLUDE[win81](../debugger/includes/win81_md.md)] als veraltet gelten.  Überprüfen Sie die Website des Anbieters des Erweiterungs\-SDKs, um zu ermitteln, ob Store\-Projekte auf es verweisen können, die auf [!INCLUDE[win81](../debugger/includes/win81_md.md)] abzielen.  
  
     Wenn Sie feststellen, dass das Erweiterungs\-SDK, auf das von Ihrer Anwendung verwiesen wird, nicht unterstützt wird, müssen Sie folgende Schritte ausführen:  
  
2.  Schauen Sie sich den Namen des Projekts an, das den Fehler verursacht.  Die Plattform, auf die Ihr Projekt abzielt, steht in Klammern neben dem Projektnamen.  Beispielsweise bedeutet **MyProjectName \(Windows 8.1\)**, dass das Projekt "MyProjectName" auf die Plattformversion [!INCLUDE[win81](../debugger/includes/win81_md.md)] abzielt.  
  
3.  Wechseln Sie zur Website des Anbieters des nicht unterstützten Erweiterungs\-SDKs, und installieren Sie die Version des Erweiterungs\-SDKs mit Abhängigkeiten, die mit der Version der Plattform kompatibel sind, auf die Ihr Projekt abzielt.  
  
4.  Wenn das zuvor installierte Erweiterung\-SDK von anderen Erweiterung\-SDKs abhängt, rufen Sie die Websites der entsprechenden Anbieter auf, und installieren Sie die Versionen, die mit der Version der Plattform kompatibel sind, auf die Ihr Projekt abzielt.  
  
    > [!NOTE]
    >  Wenn Ihr Projekt auf [!INCLUDE[win81](../debugger/includes/win81_md.md)] abzielt und das zuvor installierte Erweiterungs\-SDK von Microsoft Visual C\+\+ Runtime Package abhängt, lautet die Version von Microsoft Visual C\+\+ Runtime Package, die mit Windows 8.1 kompatibel ist, v12.0 und wird mit [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] installiert.  
  
    > [!NOTE]
    >  Um herauszufinden, ob das zuvor installierte Erweiterungs\-SDK Abhängigkeiten von anderen Erweiterungs\-SDKs aufweist, müssen Sie Visual Studio neu starten. Erstellen Sie dann ein neues C\#\-Windows Store\-Projekt, klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Verweis hinzufügen**, wechseln Sie zur Registerkarte **Windows**, wechseln Sie zur Unterregisterkarte **Erweiterungen**, wählen Sie das Erweiterungs\-SDK aus, und schauen Sie sich den rechten Bereich des **Verweis\-Managers** an.  Wenn Abhängigkeiten bestehen, werden sie dort aufgeführt.  
  
5.  Starten Sie Visual Studio neu, und öffnen Sie Ihre App.  
  
6.  Klicken Sie mit der rechten Maustaste auf das Projekt, das den Fehler verursacht, und wählen Sie bei Visual Basic\-, C\#\- oder JavaScript\-Projekten die Option **Verweis hinzufügen** oder bei C\+\+\-Projekten die Option **Verweise** aus.  Klicken Sie bei C\+\+\-Projekten dann auf die Schaltfläche "Neuen Verweis hinzufügen".  
  
7.  Klicken Sie auf die Registerkarte **Windows** und anschließend auf die Unterregisterkarte **Erweiterungen**.  Deaktivieren Sie die Kontrollkästchen neben den alten Erweiterungs\-SDKs, und aktivieren Sie die Kontrollkästchen neben den neuen Erweiterungs\-SDKs.  Klicken Sie auf **OK**.