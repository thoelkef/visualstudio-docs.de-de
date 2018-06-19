---
title: Erstellen von Optionsseiten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 51e05c5f2660adfe8d7a35c816e5f94706631c8f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131287"
---
# <a name="creating-options-pages"></a>Erstellen von Optionsseiten
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Verwaltetes Paketframework von abgeleiteten Klassen <xref:Microsoft.VisualStudio.Shell.DialogPage> erweitern die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE durch Hinzufügen von **Optionen** Seiten unter der **Tools** Menü.  
  
 Ein Objekt, durch eine angegebene **Clienttools-Option** Seite bezieht sich auf bestimmte VSPackages durch die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Objekt.  
  
 Da die Umgebung wird das Implementieren von einer bestimmtes Objekt instanziiert **Extras – Optionen** Seite, wenn diese bestimmte Seite von der IDE angezeigt wird:  
  
-   Ein **Clienttools-Option** Seite seines eigenen Objekts und nicht auf dem Objekt implementiert, eine VSPackage implementiert werden sollte.  
  
-   Ein Objekt kann nicht mehrere implementieren **Extras – Optionen** Seiten.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Registrieren als einen Extras Optionen-Seite-Anbieter  
 VSPackage unterstützenden Benutzerkonfiguration über **Extras – Optionen** Seiten gibt an, die Objekte, die diese Bereitstellung **Extras – Optionen** Seiten durch Anwenden von Instanzen von <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> angewendet, um die <xref:Microsoft.VisualStudio.Shell.Package>Implementierung.  
  
 Es muss eine Instanz des <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> für jede <xref:Microsoft.VisualStudio.Shell.DialogPage>-abgeleiteten Typ, der implementiert eine **Extras – Optionen** Seite.  
  
 Jede Instanz des <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> verwendet den Typ, implementiert die **Extras – Optionen** Seite Zeichenfolgen, die die Kategorie und Unterkategorie, die zur Identifizierung enthalten eine **Extras – Optionen** Seite und Ressource Informationen zum Registrieren des Typs als Anbieter einer **Extras – Optionen** Seite.  
  
## <a name="persisting-tools-options-page-state"></a>Zustand von beibehalten von Extras Optionen-Seite  
 Wenn eine **Extras – Optionen** -seitenimplementierung mit-Unterstützung aktiviert registriert ist, die IDE weiterhin besteht, den Zustand der Seite zusammen mit allen anderen **Extras – Optionen** Seiten.  
  
 Eine VSPackage kann über einen eigenen Persistenz verwalten <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Nur eine oder die andere Methode Persistenz sollte verwendet werden.  
  
## <a name="implementing-dialogpage-class"></a>Implementieren von DialogPage-Klasse  
 Ein Objekt, das eine VSPackage Implementierung bietet eine <xref:Microsoft.VisualStudio.Shell.DialogPage>-abgeleiteten Typ nutzen die folgenden geerbten Funktionen zu verwenden:  
  
-   Ein Standard-Benutzeroberflächenfenster.  
  
-   Ein Standard verfügbar Dauerhaftigkeit entweder If <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> auf die Klasse angewendet wird oder wenn die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> -Eigenschaftensatz auf `true` für die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> , für die Klasse angewendet wird.  
  
-   -Unterstützung.  
  
 Die Mindestanforderungen für ein Objekt, durch eine **Extras – Optionen** Seite <xref:Microsoft.VisualStudio.Shell.DialogPage> ist das Hinzufügen von öffentlichen Eigenschaften.  
  
 Die Klasse als ordnungsgemäß registriert eine **Extras – Optionen** Seite Anbieter, und klicken Sie dann auf die öffentlichen Eigenschaften zur Verfügung der **Optionen** Teil der **Tools** Menü in Form von einer das Eigenschaftenraster.  
  
 Alle diese Funktionen können überschrieben werden. So erstellen Sie einen komplexere Benutzer Schnittstelle erfordert beispielsweise nur überschreiben die standardmäßige Implementierung des <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Beispiel  
 Im folgenden ist eine einfache "hello World"-Implementierung erstellen, der eine Seite "Optionen". Erstellt den folgenden Code in ein Standardprojekt hinzufügen, indem der Visual Studio-Paketvorlage mit der **Menübefehl** gewählten Option angemessen zeigen, die Funktionen der Option-Seite.  
  
### <a name="description"></a>Beschreibung  
 Die folgende Klasse definiert eine minimale Optionsseite "hello World". Der Benutzer kann nach dem Öffnen werden Festlegen des öffentlichen `HelloWorld` Eigenschaft in einem Eigenschaftenraster.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Beschreibung  
 Das folgende Attribut anwenden, für die Paketklasse stellt die Seite Optionen zur Verfügung, wenn das Paket lädt. Die Zahlen sind beliebige Ressourcen-IDs für die Kategorie und die Seite, und am Ende der boolesche Wert gibt an, ob die Seite Automation unterstützt.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Beschreibung  
 Der folgende Ereignishandler zeigt ein Ergebnis abhängig vom Wert der Eigenschaft in der Seite "Optionen" festgelegt. Er verwendet die <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> Methode mit dem Ergebnis explizit umgewandelt, in die benutzerdefinierte Option Seitentyp Zugriff auf die Eigenschaften, die von der Seite "verfügbar gemacht werden.  
  
 Im Falle eines Projekts generiert, die für die Paket-Vorlage, mit dieser Funktion wird von der `MenuItemCallback` -Funktion für die Verbindung zu den Standardbefehl hinzugefügt, um die **Tools** Menü.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Benutzereinstellungen und Optionen](../../extensibility/extending-user-settings-and-options.md)   
 [Automatisierungsunterstützung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md)