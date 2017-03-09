---
title: "Dialogfeld &quot;Assemblyinformationen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAssemblyInfo"
helpviewer_keywords: 
  - "Assemblyinformationen (Dialogfeld)"
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Dialogfeld &quot;Assemblyinformationen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Dialogfeld **Assemblyinformationen** werden die Werte der globalen [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]\-Assemblyattribute festgelegt, die in der AssemblyInfo\-Datei gespeichert sind. Diese wird automatisch mit dem Projekt erstellt.  Im **Projektmappen\-Explorer** befindet sich die Datei im Knoten **Mein Projekt** in [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] \(klicken Sie zum Anzeigen auf **Alle Dateien anzeigen**\). Sie befindet sich unter **Eigenschaften** in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  Weitere Informationen zu Assemblyattributen finden Sie unter [Attribute](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Wählen Sie zum Aufrufen des Dialogfelds einen Projektknoten im **Projektmappen\-Explorer** aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**.  Sobald der **Projekt\-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Anwendung**.  Klicken Sie auf der Seite **Anwendung** auf die Schaltfläche **Assemblyinformationen**.  
  
## UIElement-Liste  
 **Titel**  
 Legt einen Titel für das Assemblymanifest fest.  Entspricht <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Beschreibung**  
 Gibt eine optionale Beschreibung für das Assemblymanifest an.  Entspricht <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Firma**  
 Gibt einen Firmennamen für das Assemblymanifest an.  Entspricht <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Produkt**  
 Gibt einen Produktnamen für das Assemblymanifest an.  Entspricht <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Copyright**  
 Gibt Copyrightinformationen für das Assemblymanifest an.  Entspricht <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Marke**  
 Gibt eine Marke für das Assemblymanifest an.  Entspricht <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Assemblyversion**  
 Gibt die Version der Assembly an.  Entspricht <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Dateiversion**  
 Gibt eine Versionsnummer an, die den Compiler anweist, eine bestimmte Version der Versionsressource der Win32\-Datei zu verwenden.  Entspricht <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 Eine eindeutige GUID zur Identifizierung der Assembly.  Wenn Sie ein Projekt erstellen, generiert Visual Studio eine GUID für die Assembly.  Entspricht <xref:System.Guid>.  
  
 **Neutrale Sprache**  
 Gibt an, welchen Kulturkreis die Assembly unterstützt.  Entspricht <xref:System.Resources.NeutralResourcesLanguageAttribute>.  Der Standardwert ist **\(Keine\)**.  
  
 **Assembly COM\-sichtbar machen**  
 Gibt an, ob Typen in der Assembly für COM verfügbar sind.  Entspricht <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## Siehe auch  
 [Seite "Anwendung", Projekt\-Designer \(Visual Basic\)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Attribute](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)