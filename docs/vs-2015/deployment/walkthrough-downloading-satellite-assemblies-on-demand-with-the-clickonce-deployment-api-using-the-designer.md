---
title: 'Exemplarische Vorgehensweise: Herunterladen von Satellitenassemblys bei Bedarf mit der API, die mithilfe des Designers für die ClickOnce-Bereitstellung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 559fb1f3613b42bd2c972f61b45736b07e76a318
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62420016"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Exemplarische Vorgehensweise: Herunterladen von Satellitenassemblys bei Bedarf mit der API, die mithilfe des Designers für die ClickOnce-Bereitstellung

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit Windows Forms-Anwendungen können mehrere Kulturen mithilfe von Satellitenassemblys konfiguriert werden. Eine *Satellitenassembly* ist eine Assembly, die Anwendungsressourcen für eine andere Kultur als die Standardkultur der Anwendung enthält.

Siehe [Lokalisieren von ClickOnce-Anwendungen](../deployment/localizing-clickonce-applications.md), können Sie mehrere Satellitenassemblys für mehrere Kulturen innerhalb derselben einschließen [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung. In der Standardeinstellung lädt [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] alle Satellitenassemblys in Ihrer Bereitstellung auf den Clientcomputer herunter, obwohl ein einzelner Client wahrscheinlich nur eine Satellitenassembly benötigt.

Diese exemplarische Vorgehensweise beschreibt, wie Sie Ihre Satellitenassemblys als optional kennzeichnen und nur die Assembly herunterladen, die ein Clientcomputer für die eigenen aktuellen Kultureinstellungen benötigt.

> [!NOTE]
> Zu Testzwecken legen die folgenden Codebeispiele die Kultur programmgesteuert auf `ja-JP` fest. Im Abschnitt "Nächste Schritte" weiter unten in diesem Thema finden Sie Informationen zum Anpassen dieses Codes für eine Produktionsumgebung.

### <a name="to-mark-satellite-assemblies-as-optional"></a>So markieren Sie Satellitenassemblys als optional

1. Erstellen Sie das Projekt. Dadurch werden Satellitenassemblys für alle Kulturen generiert, die Sie lokalisieren.

2. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektnamen, und klicken Sie dann auf **Eigenschaften**.

3. Klicken Sie auf die Registerkarte **Veröffentlichen**, und klicken Sie dann auf die **Anwendungsdateien**.

4. Aktivieren Sie das Kontrollkästchen **Alle Dateien anzeigen**, um Satellitenassemblys anzuzeigen. Standardmäßig werden alle Satellitenassemblys in Ihre Bereitstellung aufgenommen und in diesem Dialogfeld angezeigt.

     Eine Satellitenassembly hat einen Namen im Format *ISO-Code*\ApplicationName.Resources.dll, in denen *ISO-Code* einem Sprachenbezeichner im Format RFC 1766.

5. Klicken Sie auf **neu...**  in die **Downloadgruppe** Liste für jede Sprach-ID.. Wenn Sie zur Eingabe eines Downloadgruppennamens aufgefordert werden, geben Sie die Sprach-ID ein. Z. B. für eine japanische Satellitenassembly würden, geben Sie den Download an `ja-JP`.

6. Schließen Sie das Dialogfeld **Anwendungsdateien**.

### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>So laden Sie Satellitenassemblys bei Bedarf in C\# herunter

1. Öffnen Sie die Datei "Program.cs". Wenn diese Datei nicht im Projektmappen-Explorer angezeigt wird, wählen Sie das Projekt aus, und klicken Sie im Menü **Projekt** auf **Alle Dateien anzeigen**.

2. Verwenden Sie den folgenden Code, um die entsprechende Satellitenassembly herunterzuladen und die Anwendung zu starten.

     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssemblies/CS/Program.cs#1)]

### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>So laden Sie Satellitenassemblys bei Bedarf in Visual Basic herunter

1. Klicken Sie im Fenster **Eigenschaften** der Anwendung auf die Registerkarte **Anwendung**.

2. Klicken Sie unten auf der Registerkarte auf **Anwendungsereignisse anzeigen**.

3. Fügen Sie folgenden Importanweisungen am Anfang der Datei "ApplicationEvents.VB" hinzu.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb#1)]

4. Fügen Sie der `MyApplication` -Klasse folgenden Code hinzu.

     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesVB/VB/ApplicationEvents.vb#2)]

## <a name="next-steps"></a>Nächste Schritte

In einer Produktionsumgebung müssen Sie wahrscheinlich die Zeile in den Codebeispielen entfernen, die <xref:System.Threading.Thread.CurrentUICulture%2A> auf einen bestimmten Wert festlegt, da auf Clientcomputern der richtige Wert standardmäßig festgelegt ist. Beim Ausführen der Anwendung auf einem japanischen Clientcomputer ist <xref:System.Threading.Thread.CurrentUICulture%2A> z. B. standardmäßig `ja-JP` . Das programmgesteuerte Festlegen ist eine gute Möglichkeit, die Satellitenassemblys zu testen, bevor Sie die Anwendung bereitstellen.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Herunterladen von Satellitenassemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)
- [Lokalisieren von ClickOnce-Anwendungen](../deployment/localizing-clickonce-applications.md)
