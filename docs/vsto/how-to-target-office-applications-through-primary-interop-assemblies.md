---
title: "Verweisen auf Office-Anwendungen durch prim&#228;re Interopassemblys | Microsoft Docs"
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
helpviewer_keywords: 
  - "Anwendungsentwicklung [Office-Entwicklung in Visual Studio], Automatisieren"
  - "Assemblys [Office-Entwicklung in Visual Studio], PIA-Verweise"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Automatisieren"
  - "Primäre Interop-Assemblys von Office in Visual Studio], Hinzufügen von Verweisen zu"
  - "Primäre Interop-Assemblys [Office-Entwicklung in Visual Studio], Hinzufügen von Verweisen zu"
ms.assetid: 9bedae85-32b6-4df6-82b2-9d124fb49636
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Verweisen auf Office-Anwendungen durch prim&#228;re Interopassemblys
  Wenn Sie ein neues Office\-Projekt erstellen, fügt Visual Studio automatisch Verweise auf die primären Interopassemblys \(PIAs\) von Microsoft Office hinzu, die zum Erstellen des Projekts erforderlich sind.  Verweise auf andere PIAs müssen in den folgenden Szenarien hinzugefügt werden:  
  
-   Sie möchten Features anderer Microsoft Office\-Anwendungen im Projekt verwenden.  Sie möchten z. B. Features von Microsoft Office Excel in einem Projekt für Microsoft Office Word verwenden.  
  
-   Sie möchten Microsoft Office\-Anwendungen automatisieren, die nicht über dedizierte Projekte in Visual Studio verfügen, z. B. Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### So fügen Sie einen Verweis auf eine primäre Interopassembly hinzu  
  
1.  Öffnen Sie das Office\-Projekt, und wählen Sie im **Projektmappen\-Explorer** den Projektnamen aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen**.  
  
3.  Wählen Sie auf der Registerkarte **Framework** die primäre Interop\-Assembly \(PIA\) aus, die in der Liste **Komponentenname** enthalten sein soll.  Weitere Informationen zu den verfügbaren primären Interop\-Assemblys in Microsoft Office finden Sie unter [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md).  
  
     Wenn für das Projekt als Zielversion [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher festgelegt wird, wird die Eigenschaft **Interop\-Typen einbetten** für den Assemblyverweis standardmäßig auf **True** festgelegt.  Mit dieser Einstellung erfordert die Lösung keine PIA auf Endbenutzercomputern.  Weitere Informationen finden Sie unter [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  Fügen Sie in Office\-Projekten Verweise auf Office\-PIAs immer über die Registerkarte **.NET** im Dialogfeld **Verweis hinzufügen** hinzu anstatt über die Registerkarte **COM**.  Weitere Informationen finden Sie unter [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Klicken Sie auf **OK**.  
  
     Der Assemblyname wird im **Projektmappen\-Explorer** im Ordner **Verweise** angezeigt.  
  
## Siehe auch  
 [Primäre Interopassemblys in Office](../vsto/office-primary-interop-assemblies.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)   
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Gewusst wie: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  