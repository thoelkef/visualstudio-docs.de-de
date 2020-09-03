---
title: Erstellen von Options Seiten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c2b993a6c6947adfa3b01f2947b992b23236b8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196946"
---
# <a name="creating-options-pages"></a>Erstellen von Optionsseiten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Managed Package Framework erweitern die von abgeleiteten Klassen <xref:Microsoft.VisualStudio.Shell.DialogPage> die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE durch Hinzufügen von **options** Seiten **Tools** im Menü Extras.  
  
 Ein Objekt, das eine bestimmte **Tool Options** Seite implementiert, ist bestimmten VSPackages durch das- <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Objekt zugeordnet.  
  
 Da die Umgebung das Objekt instanziiert, das eine bestimmte **Tool Options** Seite implementiert, wenn diese bestimmte Seite von der IDE angezeigt wird:  
  
- Eine **options** Seite für Extras sollte auf Ihrem eigenen Objekt implementiert werden, nicht auf dem Objekt, das ein VSPackage implementiert.  
  
- Ein Objekt kann nicht mehrere **Tool Options** Seiten implementieren.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Registrieren als Tool Options Seiten-Anbieter  
 Ein VSPackage, das die Benutzerkonfiguration über Extras **options** Seiten unterstützt, zeigt die Objekte an, die diese **Tools-Options** Seiten bereitstellen <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> <xref:Microsoft.VisualStudio.Shell.Package>  
  
 Es muss eine Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> für jeden <xref:Microsoft.VisualStudio.Shell.DialogPage> abgeleiteten Typ vorhanden sein, der eine Extras **options** Seite implementiert.  
  
 Jede Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> verwendet den Typ, der die **options** Seite "Tools" implementiert, Zeichen folgen, die die Kategorie und die Unterkategorie enthalten, die zum Identifizieren einer Extras **Optionen** -Seite verwendet werden, und Ressourcen Informationen, um den Typ als Bereitstellung einer Extras **Optionen** -Seite zu registrieren.  
  
## <a name="persisting-tools-options-page-state"></a>Beibehalten von Tools Optionen Seiten Status  
 Wenn eine **Tools-Optionen** -Seiten Implementierung bei aktivierter Automatisierungsunterstützung registriert ist, speichert die IDE den Status der Seite zusammen mit allen anderen Extras- **options** Seiten.  
  
 Ein VSPackage kann seine eigene Persistenz mithilfe von verwalten <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . Es sollte nur eine oder die andere Persistenzmethode verwendet werden.  
  
## <a name="implementing-dialogpage-class"></a>Implementieren der DialogPage-Klasse  
 Ein Objekt, das eine VSPackage-Implementierung eines von <xref:Microsoft.VisualStudio.Shell.DialogPage> abgeleiteten Typs bereitstellt, kann die folgenden geerbten Features nutzen:  
  
- Ein Standardfenster für die Benutzeroberfläche.  
  
- Ein standardmäßiger Persistenzmechanismus <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> ist verfügbar, wenn auf die Klasse angewendet wird, oder, wenn die- <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> Eigenschaft `true` für den auf <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> die Klasse angewendeten festgelegt ist.  
  
- Automatisierungsunterstützung.  
  
  Die Mindestanforderung für ein Objekt, das eine Extras **options** Seite mithilfe von implementiert, <xref:Microsoft.VisualStudio.Shell.DialogPage> ist das Hinzufügen von öffentlichen Eigenschaften.  
  
  Wenn die Klasse ordnungsgemäß als **options** Seiten Anbieter für Extras registriert ist, sind ihre öffentlichen Eigenschaften im Abschnitt **Optionen** **des Menüs Extras** in Form eines Eigenschaften Rasters verfügbar.  
  
  Alle diese Standard Features können überschrieben werden. Zum Erstellen einer anspruchsvolleren Benutzeroberfläche ist es z. b. erforderlich, dass nur die Standard Implementierung von überschrieben wird <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> .  
  
## <a name="example"></a>Beispiel  
 Im folgenden finden Sie eine einfache "Hello World"-Implementierung einer Optionsseite. Wenn Sie den folgenden Code zu einem Standard Projekt hinzufügen, das von der Visual Studio-Paket Vorlage erstellt wurde, und die **Menübefehls** Option ausgewählt ist, wird die Option Seiten Funktionalität ordnungsgemäß  
  
### <a name="description"></a>BESCHREIBUNG  
 Die folgende Klasse definiert eine minimale "Hello World"-Optionsseite. Beim Öffnen kann der Benutzer die Public- `HelloWorld` Eigenschaft in einem Eigenschaften Raster festlegen.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>BESCHREIBUNG  
 Wenn Sie das folgende Attribut auf die Paket Klasse anwenden, ist die Seite Optionen verfügbar, wenn das Paket geladen wird. Die Zahlen sind beliebige Ressourcen-IDs für die Kategorie und die Seite, und der boolesche Wert am Ende gibt an, ob die Seite die Automatisierung unterstützt.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>BESCHREIBUNG  
 Der folgende Ereignishandler zeigt ein Ergebnis an, abhängig vom Wert der Eigenschaft, die auf der Seite Optionen festgelegt ist. Dabei wird die- <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> Methode verwendet, wobei das Ergebnis explizit in den benutzerdefinierten Options Seitentyp umgewandelt wird, um auf die von der Seite verfügbar gemachten Eigenschaften zuzugreifen.  
  
 Bei einem Projekt, das von der Paket Vorlage generiert wird, wird diese Funktion von der-Funktion aufgerufen, `MenuItemCallback` um Sie an den Standardbefehl anzufügen **, der** dem Menü Extras hinzugefügt wird.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweitern von Benutzereinstellungen und-Optionen](../../extensibility/extending-user-settings-and-options.md)   
 [Automatisierungsunterstützung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md)
