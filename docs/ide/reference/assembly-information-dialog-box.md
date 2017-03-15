---
title: "Dialogfeld „Assemblyinformationen“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 1a215cb25c14137f1ccc535833261a5bfc5f7a02
ms.lasthandoff: 02/22/2017

---
# <a name="assembly-information-dialog-box"></a>Dialogfeld "Assemblyinformationen"
Im Dialogfeld **Assemblyinformationen** werden die Werte der globalen [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]-Assemblyattribute festgelegt, die in der AssemblyInfo-Datei gespeichert sind, die mit dem Projekt automatisch erstellt wird. Im **Projektmappen-Explorer** befindet sich die Datei im Knoten **Mein Projekt** in [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] (klicken Sie zum Anzeigen auf **Alle Dateien anzeigen**). Sie befindet sich unter **Eigenschaften** in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Weitere Informationen zu Assemblyattributen finden Sie unter [Attributes (Attribute)](http://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).  
  
 Wählen Sie zum Aufrufen des Dialogfelds einen Projektknoten im **Projektmappen-Explorer** aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Wenn der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Anwendung**. Klicken Sie auf der Seite **Anwendung** auf die Schaltfläche **Assemblyinformationen**.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Titel**  
 Gibt einen Titel für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Beschreibung**  
 Gibt eine optionale Beschreibung für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Firma**  
 Gibt einen Firmennamen für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Produkt**  
 Gibt einen Produktnamen für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Copyright**  
 Gibt Copyrightinformationen für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Marke**  
 Gibt eine Marke für das Assemblymanifest an. Entspricht <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Assemblyversion**  
 Gibt die Version der Assembly an. Entspricht <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Dateiversion**  
 Gibt eine Versionsnummer an, die den Compiler anweist, eine bestimmte Version der Versionsressource der Win32-Datei zu verwenden. Entspricht <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 Eine eindeutige GUID zur Identifizierung der Assembly. Wenn Sie ein Projekt erstellen, generiert Visual Studio eine GUID für die Assembly. Entspricht <xref:System.Guid>.  
  
 **Neutrale Sprache**  
 Gibt an, welche Kultur die Assembly unterstützt. Entspricht <xref:System.Resources.NeutralResourcesLanguageAttribute>. Der Standardwert lautet **(Keine)**.  
  
 **Assembly COM-sichtbar machen**  
 Gibt an, ob Typen in der Assembly für COM verfügbar sind. Entspricht <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## <a name="see-also"></a>Siehe auch  
 [Application Page, Project Designer (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Attribute](http://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
