---
title: "Gewusst wie: Markieren von Steuerelementen als sichere Steuerelemente | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Sichere Steuerelemente [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Erweiterte Tools zum Packen"
  - "SharePoint-Entwicklung in Visual Studio, Sichere Steuerelemente"
ms.assetid: 813727d5-6750-407c-a23e-c38dd611e78c
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Gewusst wie: Markieren von Steuerelementen als sichere Steuerelemente
  Aus Sicherheitsgründen wird in SharePoint zwischen Websteuerelementen, die vor Skripteinschleusungen geschützt sind, und Websteuerelementen ohne diesen Schutz unterschieden.  Auf geschützte Steuerelemente oder *sichere Steuerelemente* kann von nicht vertrauenswürdigen Benutzern zugegriffen werden.  Sie können Steuerelemente in der Eigenschaft **Einträge für sicheres Steuerelement** eines SharePoint\-Projektelements oder im Paket\-Designer als sicher markieren, wenn Sie dem Paket eine Assembly hinzufügen.  Weitere Informationen finden Sie unter  
  
 [Einstellungs\-Änderung Datei web.config](http://go.microsoft.com/fwlink/?LinkId=178965) und [Registrieren einer Webpart\-Assemblys als sicheres Steuerelement](http://go.microsoft.com/fwlink/?LinkId=171013).  
  
> [!IMPORTANT]  
>  Diese Prozeduren dienen zur Erläuterung.  Markieren Sie Steuerelemente nur dann als sicher, wenn Sie von deren Sicherheit überzeugt sind.  
  
## Markieren sicherer Steuerelemente in der Eigenschaft "Einträge für sicheres Steuerelement"  
  
#### So markieren Sie Steuerelemente in der Eigenschaft "Einträge für sicheres Steuerelement" als sicher oder unsicher  
  
1.  Erstellen Sie eine SharePoint\-Lösung mit einem Projekt vom Typ "Visuelles Webpart".  
  
2.  Fügen Sie dem Webpart zwei Steuerelemente hinzu: ein Textfeld und eine Schaltfläche.  Behalten Sie die Standardnamen \("TextBox1" bzw. "Button1"\) bei.  
  
3.  Fügen Sie der Eigenschaft **Einträge für sicheres Steuerelement** des Webparts zwei Einträge hinzu.  Hierzu, wählen Sie die Schaltfläche mit den Auslassungszeichen \(![Auslassungszeichen im ASP.NET Mobile-Designer](../sharepoint/media/mwellipsis.png "Auslassungszeichen im ASP.NET Mobile-Designer")\) neben der Eigenschaft **Einträge für sicheres Steuerelement** im Fenster **Eigenschaften**.  
  
     Das Dialogfeld **Einträge für sicheres Steuerelement** wird angezeigt.  
  
4.  Im Dialogfeld **Einträge für sicheres Steuerelement** wählen Sie die Schaltfläche **Hinzufügen** zweimal, um zwei Einträge für sichere Steuerelemente im Bereich **Member** hinzuzufügen: ein für die Schaltfläche und einen für das Textfeld.  
  
5.  Wählen Sie den ersten Eintrag für sichere Steuerelemente, und ändern Sie dann den Wert der Eigenschaft **Sicher** in **False**, der Eigenschaft **Typname** zu **Button1** und die Eigenschaft **Sicher vor Skripteinschleusung** in **False**.  
  
     Durch diesen Schritt wird das Schaltflächen\-Steuerelement als unsicheres Steuerelement gekennzeichnet.  
  
6.  Wählen Sie den zweiten Eintrag für sichere Steuerelemente in der Liste aus.  Lassen Sie den Wert der Eigenschaft **Sicher** als **True** und legen Sie dessen Eigenschaft **Typname** auf **TextBox1** und die Eigenschaft **Sicher vor Skripteinschleusung** auf **True** fest.  
  
     Das Textfeld\-Steuerelement ist nun als Steuerelement markiert, das vor der Einschleusung von Skriptbefehlen geschützt ist.  
  
7.  Wählen Sie die Schaltfläche **OK**, um das Dialogfeld zu schließen.  
  
## Markieren sicherer Steuerelemente im Paket\-Designer  
  
#### So markieren Sie Steuerelemente im Paket\-Designer als sicher oder unsicher  
  
1.  Erstellen Sie eine SharePoint\-Lösung mit einem Projekt vom Typ "Visuelles Webpart".  
  
2.  Fügen Sie dem Webpart zwei Steuerelemente hinzu: ein Textfeld und eine Schaltfläche.  Behalten Sie die Standardnamen \("TextBox1" bzw. "Button1"\) bei.  
  
     Notieren Sie den Namespace des Steuerelements, da dieser später verwendet wird.  
  
3.  Wählen Sie in der Menüleiste **Projektmappe erstellen**, **Erstellen**, um das Projekt zu erstellen.  
  
4.  Erstellen Sie eine weitere SharePoint\-Lösung.  
  
5.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für die Package.Package\-Datei, und wählen Sie dann **Öffnen**, um **Paket\-Designer** zu öffnen.  
  
6.  Wählen Sie im **Paket\-Designer** die Registerkarte **Erweitert** aus.  
  
7.  Wählen Sie unter **Zusätzliche Assemblys** die Schaltfläche **Hinzufügen**, und wählen Sie aus der Liste **Vorhandene Assembly hinzufügen** aus.  
  
8.  Im Dialogfeld **Vorhandene Assembly hinzufügen** wählen Sie die Schaltfläche mit den Auslassungszeichen \(![Auslassungszeichen im ASP.NET Mobile-Designer](../sharepoint/media/mwellipsis.png "Auslassungszeichen im ASP.NET Mobile-Designer")\) neben **Quellpfad**.  
  
9. Wählen Sie die Assembly aus der SharePoint\-Lösung, die Sie in Schritt 1 erstellt haben, und wählen Sie dann die Schaltfläche **Öffnen** aus.  
  
10. Lassen Sie in diesem Beispiel die Option **Bereitstellungsziel** auf "GlobalAssemblyCache" festgelegt.  
  
     Durch diesen Schritt wird die Assembly im GAC \(Global Assembly Cache\) des Systems bereitgestellt.  Wenn die Assembly dagegen im Webanwendungsordner \(Ordner "Bin"\) bereitgestellt werden soll, aktivieren Sie die entsprechende Option.  Weitere Informationen finden Sie unter [Bereitstellen von Webparts in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. Im Feld **Sichere Steuerelemente** wählen Sie die Schaltfläche **Klicken Sie hier, um ein neues Element hinzuzufügen** aus.  
  
12. Geben Sie für die Eigenschaften die Werte aus der folgenden Tabelle ein:  
  
    |Eigenschaftenname|Wert|  
    |-----------------------|----------|  
    |Namespace|Der vollqualifizierte Namespace für das Steuerelement \(beispielsweise **BdcModelProject1.VisualWebPart1**\).|  
    |Typname|Button1|  
    |Assemblyname|Ein starker Assemblyname \(beispielsweise "Microsoft.Office.SharePoint.ClientExtensions, Version\=14.0.0.0, Culture\=neutral, PublicKeyToken\=71e9bce111e9429c"\).|  
    |Sicher|Deaktivieren Sie das Kontrollkästchen **Sicher**.|  
    |Sicher vor Skripteinschleusung|Lassen Sie das Kontrollkästchen **Sicher vor Skripteinschleusung** deaktiviert.|  
  
    > [!NOTE]  
    >  Der Wert **Assemblyname** für Assemblys, die im Paket\-Designer mithilfe der Registerkarte **Erweitert** hinzugefügt wurden, kann kein Token sein; es muss sich um eine Assembly mit starkem Namen handeln.  Weitere Informationen finden Sie unter [Assemblys mit starkem Namen erstellen und mit](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Drücken Sie die TAB\-TASTE, um einen weiteren Eintrag für sichere Steuerelemente zu erstellen.  
  
14. Wählen Sie die Schaltfläche **Klicken Sie hier, um ein neues Element hinzuzufügen** erneut aus.  
  
15. Geben Sie für die Eigenschaften die Werte aus der folgenden Tabelle ein:  
  
    |Eigenschaftenname|Wert|  
    |-----------------------|----------|  
    |Namespace|Der vollqualifizierte Namespace für das Steuerelement \(beispielsweise **BdcModelProject1.VisualWebPart1**\).|  
    |Typname|TextBox1|  
    |Assemblyname|Ein starker Assemblyname \(beispielsweise "Microsoft.Office.SharePoint.ClientExtensions, Version\=14.0.0.0, Culture\=neutral, PublicKeyToken\=71e9bce111e9429c"\).|  
    |Sicher|Aktivieren Sie das Kontrollkästchen **Sicher**.|  
    |Sicher vor Skripteinschleusung|Aktivieren Sie das Kontrollkästchen **Sicher vor Skripteinschleusung**.|  
  
16. Wählen Sie die TAB\-TASTE, und wählen Sie die Schaltfläche **OK**, um das Dialogfeld zu schließen.  
  
## Siehe auch  
 [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  