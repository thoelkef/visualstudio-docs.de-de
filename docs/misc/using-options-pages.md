---
title: "Verwenden von Optionsseiten | Microsoft Docs"
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
  - "Seiten „Extras – Optionen“ [Visual Studio SDK], Verwendung"
ms.assetid: 5ae6b995-3aeb-43a7-9786-4cf69faa101c
caps.latest.revision: 36
caps.handback.revision: 36
manager: "douge"
---
# Verwenden von Optionsseiten
Das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Automatisierungsmodell stellt das <xref:EnvDTE.DTE>\-Objekt zur Verfügung, das VSPackages den Zugriff auf das Dialogfeld **Optionen** im Menü **Extras** ermöglicht.  
  
 Normalerweise kann auf Seiten im Dialogfeld **Optionen** über das Automatisierungsmodell zugegriffen werden, gleich, ob die Seiten durch die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE \(Integrated Development Environment\) oder durch ein VSPackage bereitgestellt werden. Allerdings bestehen einige Ausnahmen, etwa die folgenden:  
  
-   Auf die Einstellungen der Seite **Dynamische Hilfe** kann nicht programmgesteuert zugegriffen werden. Das Feature **Dynamische Hilfe** kann mithilfe des Automatisierungsmodells gesteuert werden, jedoch muss die Steuerung direkt im Code vorgenommen werden. Weitere Informationen finden Sie unter [How to: Control the Dynamic Help Window](http://msdn.microsoft.com/de-de/7f5777aa-c270-4058-a175-8ce8a4ed25eb).  
  
-   Die Steuerung von Einstellungen auf der Seite **Schriftarten und Farben** erfolgt über deren eigene API, nicht über das Automatisierungsmodell. Weitere Informationen finden Sie unter [Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md).  
  
-   Sprachspezifische Eigenschaften können nicht über das Automatisierungsmodell abgerufen werden.  
  
 **Optionsseiten**, die das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Automatisierungsmodell nicht unterstützen, geben möglicherweise beim Abfragen keine <xref:EnvDTE.Properties>\-Sammlung für die Automatisierung zurück. Wenn die Sammlung zurückgegeben wird, enthält sie nicht alle Features. Informationen zum Verwalten dieser Features finden Sie unter [DTE\-Eigenschaftsauflistungen](../Topic/DTE%20Properties%20Collections.md).  
  
## Verwalten von Optionsseiten  
 Zum Verwalten von **Optionsseiten** muss ein VSPackage ein <xref:EnvDTE.DTE>\-Objekt beim Automatisierungsmodell abrufen.  
  
> [!NOTE]
>  Wenn ein VSPackage das Automatisierungsmodell zum Abrufen und Ändern von Einstellungen auf installierten **Optionsseiten** verwendet, erweitert es dabei den Funktionsumfang der IDE nicht. Daher muss das Paket kein Automatisierungsobjekt implementieren.  
  
 Zum Abrufen eines <xref:EnvDTE.DTE>\-Objekts mithilfe des Automatisierungsmodells rufen Sie die Methode <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> auf und geben das Dienst\-ID\-Argument `SID_SDTE` und das Schnittstellenargument `IID__DTE` an, wie hier dargestellt.  
  
```  
pServiceProvider->QueryService(SID_SDTE, IID__DTE, (LPVOID*)pDTE);  
```  
  
 Zum Abrufen eines <xref:EnvDTE.DTE>\-Objekts mithilfe des Managed Package Frameworks \(MPF\) rufen Sie die Methode <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> auf und geben einen `serviceType`\-Parameter vom Typ <xref:Microsoft.VisualStudio.Shell.Interop.SDTE> an.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#01](../extensibility/internals/codesnippet/CSharp/using-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#01](../extensibility/internals/codesnippet/VisualBasic/using-options-pages_1.vb)]  
  
 Eine **Optionsseite** wird mithilfe von zwei Bezeichnern angegeben. Der erste Bezeichner ist eine Zeichenfolge, die den Ordner angibt, der die **Optionsseite** enthält. Der zweite Bezeichner ist eine Zeichenfolge, die das spezifische Element in diesem Ordner angibt. Diese werden als Kategorie und Unterkategorie der Seite **Optionen** oder als deren Thema und Unterthema bezeichnet.  
  
 Beispielsweise befinden sich die Texteditoreinstellungen für die Verarbeitung von Basic\-Code im Navigationsbereich als Element **Basic** des Ordners **Text Editor**. Der Bezeichner für die Kategorie ist `TextEditor`, die Unterkategorie ist `Basic`, und auf die gesamte Seite **Optionen** wird als Seite `TextEditor.Basic` verwiesen.  
  
> [!NOTE]
>  Aufgrund von Lokalisierung und anderer Gründe weichen die auf der Seite **Optionen** angezeigten Namen möglicherweise von den als Kategorie\- und Unterkategoriebezeichnern verwendeten Zeichenfolgen ab. Möglicherweise müssen Sie die Automatisierung zum Abfragen der IDE verwenden, um die richtigen Bezeichner zu ermitteln, wenn sie andernorts nicht dokumentiert sind. Der Registrierungsspeicherort ist „HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<VS\-Version\>*\\AutomationProperties“, wobei *\<VS\-Version\>* die Versionsnummer der Release von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist. Weitere Informationen finden Sie unter [Registrieren benutzerdefinierter Seiten für Optionen](../misc/registering-custom-options-pages.md).  
  
 Sie können die Eigenschaften für die Seite `TextEditor.Basic` über das Automatisierungsmodell abrufen, indem Sie sich am folgenden Beispiel orientieren.  
  
```  
CComPtr<_DTE> srpDTE; CComPtr<Properties> srpDTEPropertiesList; hr = srpDTE->get_Properties("TextEditor", "Basic", &srpDTEPropertiesList);  
```  
  
 Verwenden Sie zum Abrufen der Eigenschaften mithilfe des MPFs die Methode <xref:EnvDTE._DTE.Properties%2A>.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#02](../extensibility/internals/codesnippet/CSharp/using-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#02](../extensibility/internals/codesnippet/VisualBasic/using-options-pages_2.vb)]  
  
 Die Methode <xref:EnvDTE.Properties.Item%2A> gibt einzelne Einstellungen aus der <xref:EnvDTE.Properties>\-Sammlung in Form eines <xref:EnvDTE.Property>\-Objekts zurück.  
  
 Wie bei den Kategorien und Unterkategorien weist auch hier jede Einstellung eine eindeutige Zeichenfolge als Bezeichner auf. Beispielsweise wird die Einstellung **Tabulatorgröße** auf der Seite `TextEditor.Basic` durch die Zeichenfolge `TabSize` angegeben.  
  
> [!NOTE]
>  Aufgrund von Lokalisierung und anderer Gründe weichen die auf der Seite **Optionen** angezeigten Namen möglicherweise von den als Einstellungsbezeichnern verwendeten Zeichenfolgen ab. Möglicherweise müssen Sie die Automatisierung zum Abfragen der IDE verwenden, um die richtigen Bezeichner zu ermitteln, wenn sie andernorts nicht dokumentiert sind.  
  
 Sie können den <xref:EnvDTE.Property.Value%2A> des <xref:EnvDTE.Property>\-Objekts, das von der <xref:EnvDTE.Properties.Item%2A>\-Methode der <xref:EnvDTE.Properties>\-Sammlung zurückgegeben wird, verwenden, um den Status der Einstellungen abzufragen und zu ändern.  
  
 Wenn Sie beispielsweise die Einstellung **Tabulatorgröße** auf der Seite `TextEditor.Basic` über das Automatisierungsmodell festlegen möchten, verwenden Sie das im folgenden Beispiel zurückgegebene <xref:EnvDTE.Properties>\-Objekt.  
  
```  
CComPtr<Property> srpProperty; hr = srpDTEPropertiesList->Item("TabSize", &srpProperty); hr= srpProperty.set_Value(4);  
```  
  
 Das folgende Beispiel veranschaulicht das Aktualisieren der Einstellung **Tabulatorgröße** mithilfe des MPFs.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#03](../extensibility/internals/codesnippet/CSharp/using-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#03](../extensibility/internals/codesnippet/VisualBasic/using-options-pages_3.vb)]  
  
 Weitere Informationen finden Sie unter [Steuern der Einstellungen im Dialogfeld "Optionen" \(Menü "Extras"\)](../Topic/Controlling%20Options%20Settings.md).  
  
## Beibehalten von Einstellungen für die Seite „Optionen“  
 Die IDE implementiert die Statusbeibehaltung von **Optionsseiten**, die das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Automatisierungsmodell in vollem Umfang unterstützen.  
  
 Einstellungen auf Seiten, die in der IDE enthalten sind, werden automatisch gespeichert \(oder abgerufen\), wenn ein Benutzer auf den Befehl **Einstellungen importieren\/exportieren** im Menü **Extras** klickt.  
  
 Sie können Unterstützung für diese automatische Beibehaltung für Ihre benutzerdefinierte **Optionsseite** aktivieren, indem Sie dem Registrierungseintrag der benutzerdefinierten  **Optionsseite** unter „HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<VS\-Version\>*\\AutomationProperties“ das Flag `ProfileSave` hinzufügen, wobei *\<VS\-Version\>* die Versionsnummer der Release von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bezeichnet. Weitere Informationen finden Sie unter [Registrieren benutzerdefinierter Seiten für Optionen](../misc/registering-custom-options-pages.md).  
  
## Siehe auch  
 [Erstellen von Optionsseiten mithilfe von Interop\-Assemblys](../misc/creating-options-pages-by-using-interop-assemblies.md)   
 [Optionen \(Seiten\) erstellen](../extensibility/internals/creating-options-pages.md)   
 [Erstellen von Optionsseiten mithilfe der Automatisierung](../misc/creating-options-pages-by-using-automation.md)   
 [Steuern der Einstellungen im Dialogfeld "Optionen" \(Menü "Extras"\)](../Topic/Controlling%20Options%20Settings.md)   
 [Registrieren benutzerdefinierter Seiten für Optionen](../misc/registering-custom-options-pages.md)   
 [Öffnen einer Optionsseite](../misc/opening-an-options-page.md)   
 [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)