---
title: "Gewusst wie: Debuggen einer ausf&#252;hrbaren Datei, die keiner Visual Studio-Projektmappe angeh&#246;rt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Ausführbare Dateien"
  - "Ausführbare Dateien, Debuggen außerhalb von Projekten"
  - "Ausführbare Dateien, Importieren"
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Gewusst wie: Debuggen einer ausf&#252;hrbaren Datei, die keiner Visual Studio-Projektmappe angeh&#246;rt
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Manchmal kann es erforderlich sein, eine ausführbare Datei zu debuggen, die nicht Bestandteil eines [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekts ist.  Die ausführbare Datei wurde möglicherweise außerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt, oder sie stammt von einem anderen Entwickler.  
  
 Dieses Problem wird normalerweise dadurch gelöst, dass die ausführbare Datei außerhalb von Visual Studio gestartet und mithilfe des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Debuggers angehängt wird.  Weitere Informationen finden Sie unter [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) .  
  
 Das Anfügen an eine Anwendung erfordert einige manuelle Schritte, die einige Sekunden dauern können.  Diese kurze Verzögerung hat zur Folge, dass das Anfügen keine Abhilfe schafft, wenn Sie einen Fehler debuggen, der während des Startens auftritt.  Auch beim Debuggen eines Programms, das keine Benutzereingaben erwartet und dessen Ausführung relativ schnell beendet ist, reicht die Zeit zum Anfügen u. U. nicht aus.  Wenn [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] installiert ist, können Sie für ein solches Programm ein EXE\-Projekt erstellen.  
  
### So erstellen Sie ein EXE\-Projekt für eine vorhandene ausführbare Datei  
  
1.  Klicken Sie im Menü **Datei** auf **Öffnen**, und wählen Sie **Projekt**.  
  
2.  Klicken Sie im Dialogfeld **Projekt öffnen** auf die Dropdownliste neben dem Feld **Dateiname**, und wählen Sie **Alle Projektdateien** aus.  
  
3.  Suchen Sie die ausführbare Datei, und klicken Sie auf **OK**.  
  
     Auf diese Weise wird eine temporäre Projektmappe erstellt, in der die ausführbare Datei enthalten ist.  
  
### So importieren Sie eine ausführbare Datei in eine Visual Studio\-Projektmappe  
  
1.  Zeigen Sie im Menü **Datei** auf **Projekt hinzufügen**, und klicken Sie auf **Vorhandenes Projekt**.  
  
2.  Klicken Sie im Dialogfeld **Vorhandenes Projekt hinzufügen** auf die Dropdownliste neben dem Feld **Dateiname**, und wählen Sie **Alle Projektdateien** aus.  
  
3.  Suchen Sie die ausführbare Datei, und wählen Sie sie aus.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Starten Sie die ausführbare Datei, indem Sie einen Ausführungsbefehl, z. B. **Starten**, im Menü **Debuggen** auswählen.  
  
    > [!NOTE]
    >  EXE\-Projekte werden nicht von allen Programmiersprachen unterstützt.  Installieren Sie [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], falls Sie dieses Feature benötigen.  
  
     Wenn Sie eine ausführbare Datei ohne den Quellcode debuggen, sind die verfügbaren Debugfeatures eingeschränkt, und zwar abhängig davon, ob es sich um ein Anhängen an eine laufende ausführbare Datei handelt, oder ob die ausführbare Datei einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projektmappe hinzufügt wird.  Wenn die ausführbare Datei ohne Debuginformationen in einem kompatiblen Format erstellt wurde, sind die verfügbaren Features noch weiter eingeschränkt.  Falls der Quellcode verfügbar ist, empfiehlt es sich, den Quellcode in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu importieren und ein Debugbuild der ausführbaren Datei in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu erstellen.  
  
## Siehe auch  
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [DBG Files](http://msdn.microsoft.com/de-de/91e449e9-8b65-4123-960f-2107cd1f1cfd)