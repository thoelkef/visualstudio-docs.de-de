---
title: Erstellen von Optionsseiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 076c4934fe4f81bd56edc70356ecdcc1101456e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760328"
---
# <a name="creating-options-pages"></a>Erstellen von Optionsseiten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Verwaltetes Paketframework, abgeleitete Klassen von <xref:Microsoft.VisualStudio.Shell.DialogPage> erweitern die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE durch Hinzufügen von **Optionen** Seiten unter der **Tools** Menü.  
  
 Ein Objekt, das eine angegebene **Extras/Optionen** Seite bezieht sich auf bestimmte VSPackages durch die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Objekt.  
  
 Da die Umgebung das Implementieren von einer bestimmtes Objekt instanziiert **Extras/Optionen** Seite, wenn diese bestimmte Seite von der IDE angezeigt wird:  
  
-   Ein **Extras/Optionen** Seite sollte implementiert werden, auf sein eigenes Objekt und nicht auf das Objekt, das ein VSPackage implementiert.  
  
-   Ein Objekt kann nicht mehrere implementieren **Extras/Optionen** Seiten.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Registrieren als ein Tools-Optionen-Seite-Anbieter  
 Ein VSPackage Unterstützung Benutzerkonfiguration über **Extras/Optionen** Seiten gibt an, die Objekte, die diese Bereitstellung **Extras/Optionen** Seiten durch Anwenden von Instanzen von <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> angewendet werden, um die <xref:Microsoft.VisualStudio.Shell.Package>Implementierung.  
  
 Muss eine Instanz des <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> für jede <xref:Microsoft.VisualStudio.Shell.DialogPage>-abgeleiteten Typ, der implementiert eine **Extras/Optionen** Seite.  
  
 Jede Instanz des <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> verwendet den Typ, der implementiert die **Extras/Optionen** Seite Zeichenfolgen mit der Kategorie und Unterkategorie, die zum Identifizieren einer **Extras/Optionen** Seite und Ressource Informationen zum Registrieren des Typs als Anbieter einer **Extras/Optionen** Seite.  
  
## <a name="persisting-tools-options-page-state"></a>Beibehalten von Extras Optionen-Seitenstatus  
 Wenn eine **Extras/Optionen** -seitenimplementierung mit automatisierungsunterstützung aktiviert registriert ist, behält die IDE den Zustand der Seite zusammen mit allen anderen **Extras/Optionen** Seiten.  
  
 Eine VSPackage kann über eine eigene Persistenz verwalten <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Nur eine oder die andere Methode der Persistenz sollte verwendet werden.  
  
## <a name="implementing-dialogpage-class"></a>Implementieren von DialogPage-Klasse  
 Ein Objekt, das eine VSPackage Implementierung bietet eine <xref:Microsoft.VisualStudio.Shell.DialogPage>-abgeleiteten Typ kann die folgenden geerbten Funktionen nutzen:  
  
- Ein Standard-Benutzeroberflächenfenster.  
  
- Ein Standard verfügbar persistenzmechanismus entweder If <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> auf die Klasse angewendet wird oder wenn die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> -Eigenschaftensatz auf `true` für die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> , auf die Klasse angewendet wird.  
  
- -Unterstützung.  
  
  Die Mindestanforderungen für ein Objekt, das eine **Extras/Optionen** -Seite mithilfe von <xref:Microsoft.VisualStudio.Shell.DialogPage> ist das Hinzufügen von öffentlichen Eigenschaften.  
  
  Wenn die Klasse ordnungsgemäß als registriert eine **Extras/Optionen** Seite Anbieter aus, und klicken Sie dann dessen öffentliche Eigenschaften verfügbar sind die **Optionen** im Abschnitt der **Tools** Menü in Form von einer das Eigenschaftenraster.  
  
  Alle Standardfeatures können überschrieben werden. So erstellen Sie einen komplexeren Benutzer Schnittstelle erfordert beispielsweise nur überschreiben die standardmäßige Implementierung des <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Beispiel  
 Im folgenden finden eine einfache "hello World"-Implementierung erstellen, der eine Seite mit Optionen. Der Visual Studio-Paketvorlage mit den folgenden Code hinzufügen, um ein Standardprojekt erstellt die **Menübefehl** Option ausgewählt ist angemessen Option Seite Funktionen veranschaulicht.  
  
### <a name="description"></a>Beschreibung  
 Die folgende Klasse definiert eine minimale "hello World" Seite "Optionen". Der Benutzer kann beim Öffnen, festlegen die Öffentlichkeit `HelloWorld` Eigenschaft in einem Eigenschaftenraster.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>Beschreibung  
 Das folgende Attribut für die Paketklasse angewendet stellt die Seite Optionen zur Verfügung, wenn das Paket lädt. Die Zahlen sind beliebige Ressourcen-IDs für die Kategorie und die Seite, und am Ende der boolesche Wert gibt an, ob die Seite Automatisierung unterstützt.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>Beschreibung  
 Der folgende Ereignishandler zeigt ein Ergebnis abhängig vom Wert der Eigenschaft festgelegt wird, auf der Optionsseite. Er verwendet den <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> Methode mit dem Ergebnis explizit umgewandelt werden, in die benutzerdefinierte Option Seitentyp Zugriff auf die Eigenschaften, die von der Seite verfügbar gemacht werden.  
  
 Im Falle eines Projekts, das von der Paketvorlage generiert, die mit dieser Funktion werden aus der `MenuItemCallback` -Funktion für die Verbindung mit den Standardbefehl hinzugefügt, um die **Tools** Menü.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Benutzereinstellungen und Optionen](../../extensibility/extending-user-settings-and-options.md)   
 [Automatisierungsunterstützung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md)

