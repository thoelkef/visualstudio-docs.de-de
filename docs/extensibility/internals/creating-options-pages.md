---
title: Erstellen von Optionsseiten | Microsoft-Dokumentation
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
ms.openlocfilehash: 834edb926142637a250cf4a695d5d1d54e103977
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499477"
---
# <a name="create-options-pages"></a>Erstellen von Optionsseiten
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Verwaltetes Paketframework, abgeleitete Klassen von <xref:Microsoft.VisualStudio.Shell.DialogPage> erweitern die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE durch Hinzufügen von **Optionen** Seiten unter der **Tools** Menü.  
  
 Ein Objekt, das eine angegebene **Extras/Optionen** Seite bezieht sich auf bestimmte VSPackages durch die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Objekt.  
  
 Da die Umgebung das Implementieren von einer bestimmtes Objekt instanziiert **Extras/Optionen** Seite, wenn diese bestimmte Seite von der IDE angezeigt wird:  
  
-   Ein **Extras/Optionen** Seite sollte implementiert werden, auf sein eigenes Objekt und nicht auf das Objekt, das ein VSPackage implementiert.  
  
-   Ein Objekt kann nicht mehrere implementieren **Extras/Optionen** Seiten.  
  
## <a name="register-as-a-tools-options-page-provider"></a>Registrieren Sie sich als ein Extras Optionen-Seite-Anbieter  
 Ein VSPackage Unterstützung Benutzerkonfiguration über **Extras/Optionen** Seiten gibt an, die Objekte, die diese Bereitstellung **Extras/Optionen** Seiten durch Anwenden von Instanzen von <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> angewendet werden, um die <xref:Microsoft.VisualStudio.Shell.Package>Implementierung.  
  
 Muss eine Instanz des <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> für jede <xref:Microsoft.VisualStudio.Shell.DialogPage>-abgeleiteten Typ, der implementiert eine **Extras/Optionen** Seite.  
  
 Jede Instanz des <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> verwendet den Typ, der implementiert die **Extras/Optionen** Seite Zeichenfolgen mit der Kategorie und Unterkategorie, die zum Identifizieren einer **Extras/Optionen** Seite und Ressource Informationen zum Registrieren des Typs als Anbieter einer **Extras/Optionen** Seite.  
  
## <a name="persist-tools-options-page-state"></a>Beibehalten der Seitenzustand Extras – Optionen  
 Wenn eine **Extras/Optionen** -seitenimplementierung mit automatisierungsunterstützung aktiviert registriert ist, behält die IDE den Zustand der Seite zusammen mit allen anderen **Extras/Optionen** Seiten.  
  
 Eine VSPackage kann über eine eigene Persistenz verwalten <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Nur eine oder die andere Methode der Persistenz sollte verwendet werden.  
  
## <a name="implement-dialogpage-class"></a>Implementieren von DialogPage-Klasse  
 Ein Objekt, das eine VSPackage Implementierung bietet eine <xref:Microsoft.VisualStudio.Shell.DialogPage>-abgeleiteten Typ kann die folgenden geerbten Funktionen nutzen:  
  
-   Ein Standard-Benutzeroberflächenfenster.  
  
-   Ein Standard verfügbar persistenzmechanismus entweder If <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> auf die Klasse angewendet wird oder wenn die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> -Eigenschaftensatz auf `true` für die <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> , auf die Klasse angewendet wird.  
  
-   -Unterstützung.  
  
 Die Mindestanforderungen für ein Objekt, das eine **Extras/Optionen** -Seite mithilfe von <xref:Microsoft.VisualStudio.Shell.DialogPage> ist das Hinzufügen von öffentlichen Eigenschaften.  
  
 Wenn die Klasse ordnungsgemäß als registriert eine **Extras/Optionen** Seite Anbieter aus, und klicken Sie dann dessen öffentliche Eigenschaften verfügbar sind die **Optionen** im Abschnitt der **Tools** Menü in Form von einer das Eigenschaftenraster.  
  
 Alle Standardfeatures können überschrieben werden. So erstellen Sie einen komplexeren Benutzer Schnittstelle erfordert beispielsweise nur überschreiben die standardmäßige Implementierung des <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Beispiel  
 Im folgenden finden eine einfache "Hello World"-Implementierung, der eine Seite mit Optionen. Den folgenden Code hinzufügen, um ein Standardprojekt erstellt, über die Visual Studio-Paketvorlage mit der **Menübefehl** Option ausgewählt ist angemessen Option Seite Funktionen veranschaulicht.  
  
### <a name="description"></a>Beschreibung  
 Die folgende Klasse definiert eine minimale "Hello World"-Optionen-Seite. Der Benutzer kann beim Öffnen, festlegen die Öffentlichkeit `HelloWorld` Eigenschaft in einem Eigenschaftenraster.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Beschreibung  
 Das folgende Attribut für die Paketklasse angewendet stellt die Seite Optionen zur Verfügung, wenn das Paket lädt. Die Zahlen sind beliebige Ressourcen-IDs für die Kategorie und die Seite, und am Ende der boolesche Wert gibt an, ob die Seite Automatisierung unterstützt.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Beschreibung  
 Der folgende Ereignishandler zeigt ein Ergebnis abhängig vom Wert der Eigenschaft festgelegt wird, auf der Optionsseite. Er verwendet den <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> Methode mit dem Ergebnis explizit umgewandelt werden, in die benutzerdefinierte Option Seitentyp Zugriff auf die Eigenschaften, die von der Seite verfügbar gemacht werden.  
  
 Im Falle eines Projekts, das von der Paketvorlage generiert, die mit dieser Funktion werden aus der `MenuItemCallback` -Funktion für die Verbindung mit den Standardbefehl hinzugefügt, um die **Tools** Menü.  
  
### <a name="code"></a>Code  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von benutzereinstellungen und Optionen](../../extensibility/extending-user-settings-and-options.md)   
 [Unterstützung der Automatisierung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md)