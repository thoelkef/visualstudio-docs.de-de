---
title: "Erstellen von Optionsseiten mithilfe von Interop-Assemblys | Microsoft Docs"
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
  - "Optionsseiten (Tools) [Visual Studio SDK], Erstellen mithilfe von Interop-Assemblys"
  - "Interop-Assemblys, Erstellen von Optionsseiten (Tools)"
ms.assetid: 7a03f2f5-a53e-4a46-877f-5b10dd82dbc3
caps.latest.revision: 30
caps.handback.revision: 30
manager: "douge"
---
# Erstellen von Optionsseiten mithilfe von Interop-Assemblys
Verwaltete VSPackages können die COM\-basierten Interop\-Assemblys des [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] verwenden, um die integrierte Entwicklungsumgebung \(IDE\) von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dadurch zu erweitern, dass **Optionen**\-Seiten zum Menü **Extras** hinzugefügt werden.  
  
 Eine **Extras Optionen**\-Seite ist grundsätzlich ein Benutzersteuerelement und wird in gleicher Weise codiert wie jedes andere Benutzersteuerelement. Normalerweise verwenden Sie einen der Designer der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE, um das Objekt zu erstellen und Benutzersteuerelemente hinzuzufügen.  
  
> [!NOTE]
>  Eine **Extras Optionen**\-Seite, die als Dialogfeld implementiert ist und für die eine DialogProc\-Funktion verwendet wird, um Fenstermeldungen zu verarbeiten, muss ein nicht modales Dialogfeld sein und darf nicht die EndDialog\-Funktion aufrufen.  
  
 Sie sollten das Automatisierungsobjekt verwenden, das das VSPackage für die Umgebung bereitstellt, damit die Eigenschaften unterstützt werden, die vom Benutzersteuerelement angezeigt werden.  
  
 Ein VSPackage, das eine **Extras Optionen**\-Seite implementiert, kann programmgesteuerte Kontrolle seiner Eigenschaften direkt oder über das Automatisierungsmodell der IDE unterstützen. Weitere Informationen zur Unterstützung von **Extras Optionen**\-Seiten mit Automatisierung finden Sie unter [Erstellen von Optionsseiten mithilfe der Automatisierung](../misc/creating-options-pages-by-using-automation.md).  
  
## Verfügbarmachen von Extras Optionen\-Seiten für die IDE  
 Zusätzlich zur Implementierung eines Benutzersteuerelements müssen VSPackages dieses Steuerelement für die IDE verfügbar machen.  
  
 Dies erfolgt über die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>\-Methode, die anhand der übergebenen GUID eine <xref:Microsoft.VisualStudio.Shell.Interop.VSPROPSHEETPAGE>\-Struktur zurückgibt.  
  
 Die IDE verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.VSPROPSHEETPAGE>\-Struktur, um die Eigenschaften einer **Eigenschaften**\-Seite festzulegen.  
  
 Die Einstellungen, die in ihrem `dwFlags`\-Member enthalten sind, bestimmen die genaue Interpretation der anderen Member von <xref:Microsoft.VisualStudio.Shell.Interop.VSPROPSHEETPAGE>. Die Struktur stellt in der Regel Folgendes bereit:  
  
-   Ein Handle für die Instanz, aus der eine Symbol\- oder Zeichenfolgenressource geladen werden soll  
  
-   Die Ressourcen\-ID der Dialogfeldvorlagen der Seite  
  
-   Einen Zeiger auf die DialogProc\-Funktion für die Seite  
  
## Registrieren einer Extras Optionen\-Seite  
 Sie können eine **Extras Optionen**\-Seite registrieren, indem Sie einen Eintrag im folgenden Registrierungsschlüssel erstellen: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages, wobei *\<Version\>* die Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist, etwa 8.0.  
  
 Um die Seite zu registrieren, können Sie entweder manuell die Registrierung bearbeiten oder ein Registrierungsskript \(RGS\-Datei\) verwenden. Weitere Informationen finden Sie unter [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts).  
  
## Siehe auch  
 [Erweitern der Visual Studio\-Umgebung](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)   
 [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)   
 [Benutzeroberflächenautomatisierungs\-Unterstützung für Optionen \(Seiten\)](../extensibility/internals/automation-support-for-options-pages.md)   
 [Verwenden von Optionsseiten](../misc/using-options-pages.md)   
 [Optionen \(Seiten\) erstellen](../extensibility/internals/creating-options-pages.md)   
 [Erstellen von Optionsseiten mithilfe der Automatisierung](../misc/creating-options-pages-by-using-automation.md)