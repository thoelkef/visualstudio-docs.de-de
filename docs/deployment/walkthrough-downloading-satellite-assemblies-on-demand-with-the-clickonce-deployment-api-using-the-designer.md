---
title: 'Exemplarische Vorgehensweise: Bedarfsgerechtes Herunterladen von Satellitenassemblys bei Bedarf mit der API, die mithilfe des Designers für die ClickOnce-Bereitstellung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 79c5616a9233466c71ca036c4c0cb70d43649979
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154858"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Exemplarische Vorgehensweise: Herunterladen von Satellitenassemblys bei Bedarf mit der API, die mithilfe des Designers für die ClickOnce-Bereitstellung
Mit Windows Forms-Anwendungen können mehrere Kulturen mithilfe von Satellitenassemblys konfiguriert werden. Eine *Satellitenassembly* ist eine Assembly, die Anwendungsressourcen für eine andere Kultur als die Standardkultur der Anwendung enthält.  
  
 Siehe [Lokalisieren von ClickOnce-Anwendungen](../deployment/localizing-clickonce-applications.md), können Sie mehrere Satellitenassemblys für mehrere Kulturen innerhalb derselben einschließen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung. In der Standardeinstellung lädt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] alle Satellitenassemblys in Ihrer Bereitstellung auf den Clientcomputer herunter, obwohl ein einzelner Client wahrscheinlich nur eine Satellitenassembly benötigt.  
  
 Diese exemplarische Vorgehensweise beschreibt, wie Sie Ihre Satellitenassemblys als optional kennzeichnen und nur die Assembly herunterladen, die ein Clientcomputer für die eigenen aktuellen Kultureinstellungen benötigt.  
  
> [!NOTE]
>  Zu Testzwecken legen die folgenden Codebeispiele die Kultur programmgesteuert auf `ja-JP` fest. Im Abschnitt "Nächste Schritte" weiter unten in diesem Thema finden Sie Informationen zum Anpassen dieses Codes für eine Produktionsumgebung.  
  
### <a name="to-mark-satellite-assemblies-as-optional"></a>So markieren Sie Satellitenassemblys als optional  
  
1.  Erstellen Sie das Projekt. Dadurch werden Satellitenassemblys für alle Kulturen generiert, die Sie lokalisieren.  
  
2.  Mit der rechten Maustaste auf den Projektnamen im Projektmappen-Explorer, und klicken Sie auf **Eigenschaften**.  
  
3.  Klicken Sie auf die **veröffentlichen** Registerkarte, und klicken Sie dann auf **Anwendungsdateien**.  
  
4.  Wählen Sie die **alle Dateien anzeigen** Kontrollkästchen, um Satellitenassemblys anzuzeigen. Standardmäßig werden alle Satellitenassemblys in Ihre Bereitstellung aufgenommen und in diesem Dialogfeld angezeigt.  
  
     Eine Satellitenassembly hat einen Namen im Format  *\<ISO-Code > \ApplicationName.Resources.dll*, wobei \<ISO-Code > einem Sprachenbezeichner im Format RFC 1766.  
  
5.  Klicken Sie auf **neu** in die **Downloadgruppe** Liste für jede Sprach-ID. Wenn Sie zur Eingabe eines Downloadgruppennamens aufgefordert werden, geben Sie die Sprach-ID ein. Z. B. für eine japanische Satellitenassembly würden, geben Sie den Download an `ja-JP`.  
  
6.  Schließen der **Anwendungsdateien** Dialogfeld.  
  
### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>So laden Sie Satellitenassemblys bei Bedarf in C# herunter 
  
1.  Öffnen Sie die Datei *Program.cs*. Wenn Sie nicht angezeigt werden diese Datei im Projektmappen-Explorer, wählen Sie Ihr Projekt, und auf die **Projekt** Menü klicken Sie auf **alle Dateien anzeigen**.  
  
2.  Verwenden Sie den folgenden Code, um die entsprechende Satellitenassembly herunterzuladen und die Anwendung zu starten.  
  
     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>So laden Sie Satellitenassemblys bei Bedarf in Visual Basic herunter  
  
1.  In der **Eigenschaften** Fenster für die Anwendung, klicken Sie auf die **Anwendung** Registerkarte.  
  
2.  Klicken Sie am unteren Rand der Registerkarte, auf **Anwendungsereignisse anzeigen**.  
  
3.  Fügen Sie folgenden importanweisungen am Anfang der *"ApplicationEvents.vb"* Datei.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
4.  Fügen Sie der `MyApplication`-Klasse folgenden Code hinzu.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
## <a name="next-steps"></a>Nächste Schritte  
 In einer Produktionsumgebung müssen Sie wahrscheinlich die Zeile in den Codebeispielen entfernen, die <xref:System.Threading.Thread.CurrentUICulture%2A> auf einen bestimmten Wert festlegt, da auf Clientcomputern der richtige Wert standardmäßig festgelegt ist. Beim Ausführen der Anwendung auf einem japanischen Clientcomputer ist <xref:System.Threading.Thread.CurrentUICulture%2A> z. B. standardmäßig `ja-JP` . Das programmgesteuerte Festlegen ist eine gute Möglichkeit, die Satellitenassemblys zu testen, bevor Sie die Anwendung bereitstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Herunterladen von Satellitenassemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [Lokalisieren von ClickOnce-Anwendungen](../deployment/localizing-clickonce-applications.md)
