---
title: "Seite &quot;Verweise&quot;, Projekt-Designer (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesReference"
  - "vb.ProjectPropertiesUnusedReference"
  - "vb.ProjectPropertiesReferencePaths"
helpviewer_keywords: 
  - "Seite "Verweise" im Projekt-Designer"
  - "Projekt-Designer, Seite "Verweise""
  - "Nicht verwendete Verweise (Dialogfeld)"
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Seite &quot;Verweise&quot;, Projekt-Designer (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Mithilfe der Seite **Verweise** im **Projekt\-Designer** können Sie Verweise, Webverweise und importierte Namespaces in Ihrem Projekt verwalten.  Projekte können Verweise auf COM\-Komponenten, XML\-Webdienste, .NET Framework\-Klassenbibliotheken oder \-Assemblys oder andere Klassenbibliotheken enthalten.  Weitere Informationen zur Verwendung von Verweisen finden Sie unter [Verwalten von Verweisen in einem Projekt](../../ide/managing-references-in-a-project.md).  
  
 Um auf die Seite **Verweise** zuzugreifen, wählen Sie einen Projektknoten \(nicht den **Projektmappe** Knoten\) in **Projektmappen\-Explorer**.  Wählen Sie dann **Projekt**, **Eigenschaften** auf der Menüleiste aus.  Wenn der Projekt\-Designer angezeigt wird, klicken Sie auf die Registerkarte **Verweise**.  
  
## UIElement-Liste  
 Mit den folgenden Optionen können Sie Verweise und importierte Namespaces im Projekt auswählen oder entfernen.  
  
 **Nicht verwendete Verweise**  
 Klicken Sie auf diese Schaltfläche, um auf das Dialogfeld zuzugreifen. **Nicht verwendete Verweise**  
  
 Im Dialogfeld **Nicht verwendete Verweise** können Sie Verweise entfernen, die im Projekt enthalten sind, vom Code jedoch nicht verwendet werden.  Es enthält ein Raster, das **Verweisname**, **Pfad** aufgeführt und andere Informationen über den nicht verwendeten Namespace in das Projekt verweisen.  Markieren Sie im Raster die zu entfernenden Namespaceverweise, und klicken Sie auf **Entfernen**.  
  
 **Verweispfade**  
 Klicken Sie auf diese Schaltfläche, um auf das Dialogfeld zuzugreifen. **Verweispfade**  
  
> [!NOTE]
>  Wenn das Projektsystem einen Assemblyverweis findet, löst das System den Verweis auf, indem sie an den folgenden Orten, in der folgenden Reihenfolge aussieht:  
>   
>  1.  Der Projektordner.  Die Projektordnerdateien werden in **Projektmappen\-Explorer**, wenn **Alle Dateien anzeigen** nicht aktiv ist.  
> 2.  Ordner, die im Dialogfeld **Verweispfade** angegeben werden.  
> 3.  Ordner, die Dateien im Dialogfeld **Verweis hinzufügen** anzeigen.  
> 4.  Der Ordner "obj" des Projekts.  \(Wenn Sie einen COM\-Verweis auf dem Projekt hinzufügen, werden eine oder mehrere Assemblys möglicherweise auf den Ordner "obj" des Projekts hinzugefügt.\)  
  
 **Verweise**  
 Diese Liste zeigt alle verwendeten oder nicht verwendeten Verweise im Projekt.  
  
 **add**  
 Klicken Sie auf diese Schaltfläche, um einen Verweis oder einen Webverweis zur Liste **Verweise** hinzuzufügen.  
  
 Wählen Sie **Verweis** aus, um dem Projekt im Dialogfeld "Verweis hinzufügen" einen Verweis hinzuzufügen.  
  
 Wählen Sie **Webverweis** aus, um dem Projekt im Dialogfeld "Webverweis hinzufügen" einen Webverweis hinzuzufügen.  
  
 **Entfernen**  
 Wählen Sie aus der Liste **Verweise** einen oder mehrere Verweise aus, und klicken Sie dann auf diese Schaltfläche, um sie zu löschen.  
  
 **Webverweis aktualisieren**  
 Wählen Sie aus der Liste **Verweise** einen Webverweis aus, und klicken Sie auf diese Schaltfläche, um ihn zu aktualisieren.  
  
 **Importierte Namespaces**  
 Sie können Ihren eigenen Namespace in dieses Feld eingeben und ihn durch Klicken auf **Benutzerimport hinzufügen** zur Liste mit den Namespaces hinzufügen.  
  
 Sie können Aliase für von Benutzern importierte Namespaces erstellen.  Dazu geben Sie den Alias und den Namespace im Format *Alias*\=*Namespace* ein.  Dies ist nützlich, wenn Sie lange Namespaces verwenden, z. B.: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.  
  
 **Benutzerimport hinzufügen**  
 Klicken Sie auf diese Schaltfläche, um den im Feld **Importierte Namespaces** angegebenen Namespace zur Liste der importierten Namespaces hinzuzufügen.  Die Schaltfläche ist nur aktiv, wenn der angegebene Namespace noch nicht in der Liste enthalten ist.  
  
 **Liste Namespaces**  
 Diese Liste zeigt alle verfügbaren Namespaces an.  Die Kontrollkästchen für die im Projekt enthaltenen Namespaces sind aktiviert.  
  
 **Benutzerimport aktualisieren**  
 Wählen Sie einen benutzerdefinierten Namespace aus der Liste der Namespaces aus, geben Sie im Feld **Importierte Namespaces** den ersetzenden Namen ein, und klicken Sie anschließend auf diese Schaltfläche, um den Namen zu ändern.  Die Schaltfläche ist nur aktiv, wenn der ausgewählte Namespace zuvor mithilfe der Schaltfläche **Benutzerimport hinzufügen** der Liste hinzugefügt wurde.  Folgendes kann hinzugefügt werden:  
  
-   Klassen oder Namespaces, z. B. <xref:System.Math?displayProperty=fullName>.  
  
-   Importe mit zugewiesenen Aliasen, z. B. `VB=Microsoft.VisualBasic`.  
  
-   XML\-Namespaces, z. B. `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.  
  
## Siehe auch  
 [Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds "Verweise hinzufügen"](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Gewusst wie: Hinzufügen oder Entfernen von importierten Namespaces \(Visual Basic\)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)   
 [NIB: Add Web Reference Dialog Box](http://msdn.microsoft.com/de-de/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [Imports Statement \(XML Namespace\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)