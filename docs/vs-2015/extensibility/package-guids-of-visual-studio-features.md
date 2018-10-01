---
title: Paket-GUIDs von Visual Studio-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C package GUIDs
ms.assetid: f56f0356-f3ac-48bc-9674-94259e29a4df
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb8263c3f36e4633cdc81b179f10587a3bfa0e8b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515663"
---
# <a name="package-guids-of-visual-studio-features"></a>Paket-GUIDs von Visual Studio-Funktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [-Paket-GUIDs von Visual Studio-Features](https://docs.microsoft.com/visualstudio/extensibility/package-guids-of-visual-studio-features).  
  
Sie können die folgenden GUIDs in der pkgundef-Datei Ihrer isolierten Shell-Anwendung verwenden, um bestimmte Pakete aus der Anwendung zu auszuschließen.  
  
## <a name="package-guids"></a>Paket-GUIDs  
  
|Bereich „Funktionen“|RAW-Paketname|Paket-GUID|  
|------------------|----------------------|------------------|  
|Core-IDE|Rückgängig: Paket|{1D76B2E0-F11B-11D2-AFC3-00105A9991EF}|  
||Visual Studio-Umgebungspakets|{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}|  
||Paket für die Definition von Visual Studio-Befehle|{44E07B02-29A5-11D3-B882-00C04F79F802}|  
||Paket von Visual Studio-Verzeichnis auflisten|{5010C52F-44AB-4051-8CE1-D36C20D989B4}|  
||Allgemeine Visual Studio-IDE-Paket|{6E87CFAD-6C05-4ADF-9CD7-3B7943875B7C}|  
||Visual Studio-Umgebung im Menü-Paket|{715F10EB-9E99-11D2-BFC2-00C04F990235}|  
||Visual Studio COM +-Bibliotheks-Manager-Paket|{ED8979BC-B02F-4dA9-A667-D3256C36220A}|  
||Visual Studio-Integration Quellcodeverwaltungspaket|{53544C4D-E3F8-4AA0-8195-8A8D16019423}|  
||Visual Studio-Build-Lösungspakets|{282BD676-8B5B-11D0-8A34-00A0C91E2ACD}|  
||Text-Verwaltungspaket|{F5E7E720-1401-11d1-883B-0000F87579D2}|  
||Visual Studio VsSettings-Paket|{F74C5077-D848-4630-80C9-B00E68A1CA0C}|  
|Help|Hilfe zu Visual Studio-Paket|{4A791146-19E4-11D3-B86B-00C04F79F802}|  
|Aufgabenliste, Fehlerliste|ErrorListPackage|{4A9B7E50-AA16-11D0-A8C5-00A0C921A4D2}|  
|Gliederung der Klasse|Class-Gliederung-Paket|{21AF45B0 FFA5 - 11-D 0-G63F-00A0C922E851}|  
|Installer für Toolbox-Steuerelemente|Installer-Paket für Toolbox-Steuerelemente|{2C298B35-07DA-45F1-96A3-BE55D91C8d7A}|  
|Webprojekte|Microsoft.VisualStudio.Web|{349C5850-65DF-11DA-9384-00065B846F21}|  
||Visual Web Developer-Projektpaket System|{39C9C826-8EF8-4079-8C95-428F5B1C323F}|  
||Visual Web Developer-Projektpaket Persistenz|{8FF02D1A-C177-4AC8-A62F-88FC6EA65F57}|  
||Visual Web Developer Migration Webpaket|{C1DAB116-2D63-493A-B970-10D7DD0B476E}|  
||Visual Web Developer-Webpakets|{E7f851C8-6267-4794-B0FE-7BCAB6DACBB4}|  
||Visual Web Developer Web|{DC7F691A-91FC-4F7B-923E-FE829C3A18DC}|  
|HTML-Editor|Visual Studio HTM-Editorpaket|{1B437D20-F8FE-11D2-A6AE-00104BCC7269}|  
||Visual Web Developer HTML Quellen-Editor-Paket|{BFCC0C3C-6F87-4285-A6C8-BB616061800D}|  
|CSS-Editor|Bearbeiten von Visual Studio CSS-Paket|{A764E895-518D-11d2-9A89-00C04F79EFC3}|  
|XML-Editor|Visual Studio-XML-Editor-Paket|{87569308-4813-40A0-9CD0-D7A30838CA3F}|  
|Webbrowser|Visual Studio Web-Browser-Paket|{E8B06F41-6D01-11D2-AA7D-00C04F990343}|  
||Web Application-Projekt-Factory, für die Ansicht im Webbrowser-Funktionen|{349C5851-65DF-11DA-9384-00065B846F21}|  
|Binär-Editor|Binär-Editor von Visual Studio-Paket|{5B98C2C0-CD7B-11D0-92DF-00A0C9138C45}|  
|Windows Forms-Designer|Windows Forms Designer Hosting-Pakets|{68939055-38E0-4D17-92CB-8909710D8178}|  
||Windows Forms-Designer-Paket|{7494682B-37A0-11D2-A273-00C04F8EF4FF}|  
||Windows Forms-Ressourcen-Designer-Paket|{7B5D447B-0B12-41EA-A84E-C822034422D4}|  
||Konfigurationspaket für Windows Forms-Anwendung|{80C7728B-70A6-4528-8669-73E02D1B9C41}|  
||ElementHost-Designer-Paket|{7EAB3C71-59FF-4571-A5F3-643F255FC2E6}|  
|Debugger-Benutzeroberfläche|Visual Studio Debugger|{C9DD4A57-47FB-11D2-83E7-00C04F9902C1}|  
|Datenbanktools|Visual Database Tools-Pakets|{220A4C17-7E7C-4663-BBCC-5E607C6543CD}|  
||Designer in Visual Studio Database Tools|{EF828E39-70F5-4b8e-A3A0-4C0ECD28A69A}|  
||Daten-Designer von Visual Studio|{D6C919AA-1217-41E2-a13B-9B92E1866305}|  
||Visual Studio-Daten-Paket|{E1AA7737-69BE-43d0-A425-E3097651E192}|  
||Visual Studio-Daten-Designer-Erweiterbarkeit-Paket|{A8F602E2-40CE-4dAF-AE82-A457A91728B9}|  
||Visual Studio-Explorern und Designer-Paket|{8D8529D3-625D-4496-8354-3DAD630ECC1B}|  
||Microsoft Berichts-Designer|{F3A96850-E2AE-4E00-9278-8FE23F225A0D}|  
|DSL-Laufzeit|CommonModelingPackage|{D1091694-EA72-4BDD-8918-78324CC25448}|  
||Microsoft.VisualStudio.TextTemplating|{A9696DE6-E209-414D-BBEC-A0506fb0E924}|  
|SourceSafe-Unterstützung|Visual SourceSafe-Anbieterpaket|{AA8EB8CD-7A51-11D0-92C3-00A0C9138C45}|  
||Anbieter von Visual SourceSafe-Stubpaket|{53544C4D-B03D-4209-A7D0-D9DD13A4019B}|  
|WPF-Designer|WPFFlavor.WPFPackage|{B3BAE735-386C-4030-8329-EF48EEDA4036}|  
||XamlDesignerPackage|{512be089-83ec-4cc6-8483-cf16565ae209}|  
||XamlLanguagePackage|{2ef1ec52-c8bf-4fe0-8ece-ba9c0d5d1603}|  
||XamlDiagnosticsPackage|{8291c340-36b8-4c91-8c40-cce75398ff75}|  
|Codeausschnitte|Visual Studio Code Snippets-Paket|{0B680757-2C29-4531-80FA-535A5178AA98}|  
|Verwaltet die sprachunterstützung für Projekt|Enumerator für Visual Studio-Komponente|{588205E0-66e0-11D3-8600-00C04F6123B3}|  
||Visual Studio-Einstellungen und Projekt-Designer-Paket|{67909B06-91E9-4F3E-AB50-495046BE9A9A}|  
|Exportieren Sie Vorlage...|Vorlagenpaket exportieren|{F1E4CFCA-4573-4345-8718-7BDE2b1F0BE8}|  
  
 Einige Pakete sollten niemals entfernt werden, da viele andere Features diese Abhängigkeiten übernehmen. Die aufgelisteten unter "Core-IDE" sollte beispielsweise niemals entfernt werden.  
  
 Einige Funktionen werden nicht vollständig entfernt. Beispielsweise ist kein Paket, das nicht registriert werden kann, um entfernen **Klassenansicht** und seine zugehörigen Menüs, Optionen und Dienste. Die **Klassenansicht** Fenster wird von der Visual Studio-Umgebung-Paket, das die andere wichtige IDE-Features ermöglicht bereitgestellt. Wenn Sie entfernen möchten **Klassenansicht**, man musste auch entfernen **suchen und Ersetzen**, die Umgebung **Optionen** Seiten, die **Befehlsfenster**, und die **Ausgabe** Fenster.

