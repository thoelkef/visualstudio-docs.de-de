---
title: "Optionen (Seiten) erstellen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "verwaltete Paketframework Optionsseiten im Menü Extras erstellen"
  - "Tools Optionsseiten [Visual Studio SDK] Paketframework verwaltet erstellen mit"
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Optionen (Seiten) erstellen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwalteten Paketframework von abgeleiteten Klassen <xref:Microsoft.VisualStudio.Shell.DialogPage> erweitern die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE durch Hinzufügen von **Optionen** Seiten unter den **Tools** Menü.  
  
 Ein Objekt, das einen bestimmten **Clienttools** Seite bestimmte VSPackages von zugeordnet ist die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Objekt.  
  
 Da die Umgebung das Implementieren von einer bestimmtes Objekt instanziiert **Optionen** Seite, wenn diese bestimmte Seite von der IDE angezeigt wird:  
  
-   Ein **Tools Option** Seite implementiert werden sollte, auf sein eigenes Objekt und nicht auf das Objekt, das ein VSPackage implementieren.  
  
-   Ein Objekt kann nicht mehrere implementieren **Optionen** Seiten.  
  
## Als Tools Optionen Seite Anbieter registrieren  
 VSPackage unterstützenden Benutzerkonfiguration durch **Tooloptionen** Seiten zeigt die Objekte, die diese Bereitstellung **Tooloptionen** Seiten durch Anwenden von Instanzen von <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> angewendet, um die <xref:Microsoft.VisualStudio.Shell.Package> Implementierung.  
  
 Muss eine Instanz des <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> für jede <xref:Microsoft.VisualStudio.Shell.DialogPage>\-abgeleiteten Typ, der implementiert eine **Optionen** Seite.  
  
 Jede Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> verwendet, die implementiert die **Tooloptionen** Seite Zeichenfolgen, die die Kategorie und Unterkategorie, die zur Identifikation des enthalten eine **Tooloptionen** Seite und Ressourcen zum Registrieren des Typs Bereitstellen einer **Tooloptionen** Seite.  
  
## Extras Optionen Seitenzustands  
 Wenn ein **Optionen** Seite\-Implementierung für Benutzeroberflächenautomatisierungs\-Unterstützung aktiviert registriert ist, behält die IDE den Zustand der Seite zusammen mit allen anderen **Optionen** Seiten.  
  
 Ein VSPackage kann über einen eigenen Persistenz verwalten <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Nur eine oder die andere Methode der Dauerhaftigkeit sollte verwendet werden.  
  
## Implementieren von DialogPage\-Klasse  
 Ein Objekt, das ein VSPackage\-Implementierung von einem <xref:Microsoft.VisualStudio.Shell.DialogPage>\-abgeleiteten Typ nutzen die folgenden geerbten Funktionen:  
  
-   Eine Standard\-Benutzeroberflächenfenster.  
  
-   Ein Standard Dauerhaftigkeitsmechanismus verfügbar entweder If <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> auf die Klasse angewendet wird oder wenn die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> \-Eigenschaft auf festgelegt ist `true` für die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> die auf die Klasse angewendet wird.  
  
-   Benutzeroberflächenautomatisierungs\-Unterstützung.  
  
 Die Mindestanforderung für ein Objekt, das eine **Optionen** mit der <xref:Microsoft.VisualStudio.Shell.DialogPage> ist das Hinzufügen von öffentlichen Eigenschaften.  
  
 Wenn die Klasse als ordnungsgemäß registriert eine **Tooloptionen** Seite Anbieter, dessen öffentliche Eigenschaften verfügbar sind die **Optionen** im Abschnitt der **Tools** Menü in Form von einem Eigenschaftenraster.  
  
 Alle diese Funktionen können überschrieben werden. Benutzer erstellen Schnittstelle erfordert beispielsweise nur überschreiben die standardmäßige Implementierung des <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## Beispiel  
 Im folgenden ist eine einfache "hello World"\-Implementierung eine Seite "Optionen". Der Visual Studio\-Paketvorlage mit den folgenden Code hinzufügen, um ein Standardprojekt erstellt die **Menübefehl** Option ausgewählt wird die Option Seitenfunktionalität angemessen erläutert.  
  
### Beschreibung  
 Die folgende Klasse definiert eine minimale Optionsseite "hello World". Beim Öffnen der Benutzer kann festlegen, die öffentliche `HelloWorld` Eigenschaft in einem Eigenschaftenraster.  
  
### Code  
 [!code-cs[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### Beschreibung  
 Das folgende Attribut auf die Paketklasse angewendet stellt die Seite Optionen zur Verfügung, wenn das Paket lädt. Die Zahlen sind beliebige Ressourcen\-IDs für die Kategorie und der Seite, und am Ende der boolesche Wert gibt an, ob die Seite Automatisierung unterstützt.  
  
### Code  
 [!code-cs[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### Beschreibung  
 Der folgenden Ereignishandler zeigt abhängig vom Wert der Eigenschaft auf der Optionsseite festgelegt. Er verwendet die <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> Methode mit dem Ergebnis explizit umgewandelt werden, in die benutzerdefinierte Option Seitentyp Zugriff auf die Eigenschaften, die von der Seite verfügbar gemacht werden.  
  
 Bei einem Projekt von der Paketvorlage generiert, die mit dieser Funktion werden aus der `MenuItemCallback` \-Funktion für die Verbindung zu den Standardbefehl hinzugefügt, um die **Tools** Menü.  
  
### Code  
 [!code-cs[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## Siehe auch  
 [Erweitern von Benutzereinstellungen und Optionen](../../extensibility/extending-user-settings-and-options.md)   
 [Benutzeroberflächenautomatisierungs\-Unterstützung für Optionen \(Seiten\)](../../extensibility/internals/automation-support-for-options-pages.md)