---
title: "Exemplarische Vorgehensweise: Erweitern verwalteter VSPackages durch Automatisierung | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Verwaltete VSPackages, Erweiterung durch Automatisierung"
  - "Automatisierung [Visual Studio SDK], Exemplarische Vorgehensweisen"
  - "Automatisierung [Visual Studio SDK], Verwaltete VSPackages"
ms.assetid: 7fd2000b-8ec3-4d83-b169-d38008fb57ee
caps.latest.revision: 35
caps.handback.revision: 35
manager: "douge"
---
# Exemplarische Vorgehensweise: Erweitern verwalteter VSPackages durch Automatisierung
In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie mithilfe der Automatisierung ein verwaltetes VSPackage erstellen, das die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE \(Integrierte Entwicklungsumgebung\) verändert. Sie erstellen ein Beispiel für ein verwaltetes VSPackage und zeigen dann mithilfe der Automatisierungsmethoden im resultierenden VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Eigenschaften im **Ausgabefenster** an.  
  
## Vorbereitungsmaßnahmen  
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Speicherorte für die VSPackage\-Projektvorlage  
 Die VSPackage\-Projektvorlage finden Sie an drei verschiedenen Stellen im Dialogfeld **Neues Projekt**:  
  
1.  Unter Visual Basic\-Erweiterungen. Die Standardsprache des Projekts ist Visual Basic.  
  
2.  Unter C\#\-Erweiterungen. Die Standardsprache des Projekts ist C\#.  
  
3.  Unter den Erweiterungen für andere Projekttypen. Die Standardsprache des Projekts ist C\+\+.  
  
### So erstellen Sie ein verwaltetes VSPackage  
  
1.  Erstellen Sie ein [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Package\-Projekt mit dem Namen `Auto`.  
  
     Weitere Informationen zum Erstellen eines verwalteten VSPackage finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Menübefehls mithilfe der Visual Studio\-Paketvorlage](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  Legen Sie auf der Seite **Wählen Sie eine Programmiersprache aus**[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] als Programmiersprache fest.  
  
3.  Übernehmen Sie die Standardwerte auf der Seite **Grundlegende Informationen zum VSPackage**.  
  
4.  Aktivieren Sie auf der Seite **Optionen für das VSPackage auswählen** das Kontrollkästchen **Menübefehl**.  
  
5.  Ändern Sie auf der Seite **Befehlsoptionen** den **Befehlsnamen** in `Auto`.  
  
6.  Klicken Sie auf die Schaltfläche **Fertig stellen**.  
  
     Die Vorlage generiert ein verwaltetes Projekt mit dem Namen "Auto".  
  
7.  Erstellen Sie die Projektmappe, und stellen Sie sicher, dass sie fehlerfrei kompiliert wird.  
  
### So rufen Sie das Automatisierungsmodell auf  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Projektknoten "Auto", und klicken Sie anschließend auf **Hinzufügen**, **Verweis**.  
  
2.  Doppelklicken Sie auf der Registerkarte **.NET** im Dialogfeld **Verweis** auf **EnvDTE**.  
  
     Dadurch wird ein Verweis auf den EnvDTE\-Namespace für die Automatisierung hinzugefügt.  
  
3.  Fügen Sie der Datei "AutoPackage" den folgenden Namespaceverweis hinzu.  
  
     [!code-cs[VSSDKAuto#1](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_1.cs)]
     [!code-vb[VSSDKAuto#1](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_1.vb)]  
  
4.  Ersetzen Sie in der Datei "AutoPackage" den Text der `MenuItemCallback`\-Methode durch die folgenden Zeilen:  
  
     [!code-cs[VSSDKAuto#2](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_2.cs)]
     [!code-vb[VSSDKAuto#2](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_2.vb)]  
  
 Dieser Code ruft <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> auf, um ein <xref:EnvDTE.DTE>\-Automatisierungsobjekt abzurufen, das die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE darstellt. Der Automatisierungscode in `MenuItemCallback` erstellt einen neuen Bereich im **Ausgabefenster** mit dem Namen **Test**. Name und Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] werden in den neuen **Ausgabebereich** geschrieben.  
  
1.  Erstellen und starten Sie das Projekt "Auto" im Debugmodus, indem Sie F5 drücken.  
  
     Dadurch wird das experimentelle Build von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp\) gestartet.  
  
    > [!NOTE]
    >  Zu diesem Zeitpunkt sind beide Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] geöffnet.  
  
2.  Klicken Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp im Menü **Extras** auf **Auto**.  
  
     Ein neuer Bereich mit dem Namen **Test** wird im **Ausgabefenster** geöffnet und enthält Folgendes:  
  
    ```  
    Name is Microsoft Visual Studio Version is x.xx  
    ```  
  
     Dabei ist x.xx die aktuelle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Versionsnummer.  
  
     Weitere Informationen zu Automatisierungsbeispielen finden Sie unter [Automatisierungsbeispiele für Visual Studio](http://www.microsoft.com/downloads/details.aspx?familyid=3ff9c915-30e5-430e-95b3-621dccd25150&displaylang=en).  
  
## Siehe auch  
 [Erweitern der Visual Studio\-Umgebung](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)