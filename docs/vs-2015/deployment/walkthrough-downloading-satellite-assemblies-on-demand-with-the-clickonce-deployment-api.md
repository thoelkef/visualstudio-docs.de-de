---
title: 'Exemplarische Vorgehensweise: Bedarfsgerechtes Herunterladen von Satellitenassemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: dfd9b73b7cd12108f86f566eb8d1d4a1c3823f4f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509340"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Exemplarische Vorgehensweise: Herunterladen von Satellitenassemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Exemplarische Vorgehensweise: Bedarfsgerechtes Herunterladen von Satellitenassemblys bei Bedarf mit der ClickOnce-Bereitstellung-API](https://docs.microsoft.com/visualstudio/deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api).  
  
Mit Windows Forms-Anwendungen können mehrere Kulturen mithilfe von Satellitenassemblys konfiguriert werden. Eine *Satellitenassembly* ist eine Assembly, die Anwendungsressourcen für eine andere Kultur als die Standardkultur der Anwendung enthält.  
  
 Siehe [Lokalisieren von ClickOnce-Anwendungen](../deployment/localizing-clickonce-applications.md), können Sie mehrere Satellitenassemblys für mehrere Kulturen innerhalb derselben einschließen [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung. In der Standardeinstellung lädt [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] alle Satellitenassemblys in Ihrer Bereitstellung auf den Clientcomputer herunter, obwohl ein einzelner Client wahrscheinlich nur eine Satellitenassembly benötigt.  
  
 Diese exemplarische Vorgehensweise beschreibt, wie Sie Ihre Satellitenassemblys als optional kennzeichnen und nur die Assembly herunterladen, die ein Clientcomputer für die eigenen aktuellen Kultureinstellungen benötigt. Im nachfolgend dargestellten Verfahren werden die im [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] verfügbaren Tools verwendet. Sie können diese Aufgabe auch in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausführen.  Siehe auch [Exemplarische Vorgehensweise: Bedarfsgerechtes Herunterladen von Satellitenassemblys mit der API für die ClickOnce-Bereitstellung unter Verwendung des Designers](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) oder [Exemplarische Vorgehensweise: Bedarfsgerechtes Herunterladen von Satellitenassemblys mit der API für die ClickOnce-Bereitstellung unter Verwendung des Designers](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
>  In den folgenden Codebeispielen wird die Kultur zu Testzwecken programmgesteuert auf `ja-JP`festgelegt. Im Abschnitt "Nächste Schritte" weiter unten in diesem Thema finden Sie Informationen zum Anpassen dieses Codes für eine Produktionsumgebung.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 In diesem Thema wird davon ausgegangen, dass Sie wissen, wie der Anwendung mit Visual Studio lokalisierte Ressourcen hinzugefügt werden können. Ausführliche Anweisungen finden Sie unter [Exemplarische Vorgehensweise: Lokalisieren von Windows Forms](https://msdn.microsoft.com/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>So laden Sie Satellitenassemblys bei Bedarf herunter  
  
1.  Fügen Sie den folgenden Code der Anwendung hinzu, um das bedarfsabhängige Herunterladen von Satellitenassemblys zu aktivieren.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs#1)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb#1)]  
  
2.  Generieren von Satellitenassemblys für Ihre Anwendung mithilfe von [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) oder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
3.  Generieren Sie ein Anwendungsmanifest, oder öffnen Sie das vorhandene Anwendungsmanifest, indem Sie MageUI.exe verwenden. Weitere Informationen zu diesem Tool finden Sie unter [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
4.  Klicken Sie auf die Registerkarte **Dateien** .  
  
5.  Klicken Sie auf die Schaltfläche mit den **Auslassungszeichen** (**...**), und wählen Sie das Verzeichnis aus, das alle Assemblys und Dateien der Anwendung enthält, einschließlich der Satellitenassemblys, die Sie mit Resgen.exe generiert haben. (Der Name einer Satellitenassembly hat folgendes Format: *ISO-Code*\Anwendungsname.resources.dll. Dabei entspricht *ISO-Code* einem Sprachenbezeichner im Format RFC 1766.)  
  
6.  Klicken Sie auf **Auffüllen** , um die Dateien zu Ihrer Bereitstellung hinzuzufügen.  
  
7.  Aktivieren Sie für jede Satellitenassembly das Kontrollkästchen **Optional** .  
  
8.  Legen Sie für das Gruppenfeld jeder Satellitenassembly ihren ISO-Sprachenbezeichner fest. Für eine japanische Satellitenassembly würden Sie beispielsweise den Downloadgruppennamen `ja-JP`verfügbaren Tools verwendet. Damit kann der Code, den Sie in Schritt 1 hinzugefügt haben, je nach der Einstellung der <xref:System.Threading.Thread.CurrentUICulture%2A> -Benutzereigenschaft die entsprechende Satellitenassembly herunterladen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In einer Produktionsumgebung müssen Sie im Codebeispiel wahrscheinlich die Zeile entfernen, die für <xref:System.Threading.Thread.CurrentUICulture%2A> einen bestimmten Wert festlegt, denn auf Clientcomputern ist standardmäßig der richtige Wert festgelegt. Beim Ausführen der Anwendung auf einem japanischen Clientcomputer ist <xref:System.Threading.Thread.CurrentUICulture%2A> z. B. standardmäßig `ja-JP` . Diesen Wert programmgesteuert festzulegen bietet eine gute Möglichkeit zum Testen Ihrer Satellitenassemblys, bevor Sie Ihre Anwendung bereitstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Lokalisieren von ClickOnce-Anwendungen](../deployment/localizing-clickonce-applications.md)



