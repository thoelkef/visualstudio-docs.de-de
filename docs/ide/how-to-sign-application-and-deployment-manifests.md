---
title: 'Vorgehensweise: Signieren von Anwendungs- und Bereitstellungsmanifesten | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
caps.latest.revision: 58
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: a3c0f4d3bde8bb03d3766383eba01665e58458be
ms.openlocfilehash: 18f1ea2f5ee76f4f8457b7254ff3dd3b7b3e4901
ms.contentlocale: de-de
ms.lasthandoff: 08/01/2017

---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Gewusst wie: Signieren von Anwendungs- und Bereitstellungsmanifesten
Wenn Sie eine Anwendung mit der ClickOnce-Bereitstellung veröffentlichen möchten, müssen Anwendungs- und Bereitstellungsmanifeste mit einem öffentlichen/privaten Schlüsselpaar und unter Verwendung von Authenticode signiert werden. Sie können die Manifeste mit einem Zertifikat aus dem Windows-Zertifikatspeicher oder einer Schlüsseldatei signieren.  
  
 Weitere Informationen über die ClickOnce-Bereitstellung finden Sie unter [ClickOnce-Sicherheit und Bereitstellung](../deployment/clickonce-security-and-deployment.md).  
  
 Das Signieren der ClickOnce-Manifeste ist für EXE-basierte Anwendungen optional. Weitere Informationen finden Sie im Abschnitt "Generieren von unsignierten Manifesten" in diesem Dokument.  
  
 Weitere Informationen zum Erstellen von Schlüsseldateien finden Sie unter [Vorgehensweise: Erstellen eines öffentlichen/privaten Schlüsselpaars](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unterstützt nur PFX-Schlüsseldateien (Personal Information Exchange). Sie können jedoch andere Typen von Zertifikaten aus dem Windows-Zertifikatspeicher des aktuellen Benutzers auswählen, indem Sie auf der Seite **Signierung** der Projekteigenschaften auf **Aus Speicher auswählen** klicken.  
  
### <a name="to-sign-application-and-deployment-manifests-using-a-certificate"></a>So signieren Sie Anwendungs- und Bereitstellungsmanifeste mit einem Zertifikat  
  
1.  Navigieren Sie zum Projekteigenschaftenfenster (klicken Sie mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer**, und wählen Sie **Eigenschaften** aus, geben Sie **Projekteigenschaften** im Fenster **Schnellstart** ein, oder drücken Sie innerhalb des Fensters **Projektmappen-Explorer** ALT+EINGABE). Aktivieren Sie auf der Registerkarte **Signierung** das Kontrollkästchen **ClickOnce-Manifeste signieren**.  
  
2.  Klicken Sie auf die Schaltfläche **Aus Speicher auswählen**.  
  
     Das Dialogfeld **Zertifikat auswählen** wird mit dem Inhalt des Windows-Zertifikatspeichers angezeigt.  
  
    > [!TIP]
    >  Wenn Sie auf **Klicken Sie hier, um Zertifikateigenschaften anzuzeigen** klicken, wird das Dialogfeld **Zertifikatdetails** angezeigt. Dieses Dialogfeld enthält ausführliche Informationen zu dem Zertifikat sowie zusätzliche Optionen. Sie können auf **Zertifikate** klicken, um weitere Hilfeinformationen anzuzeigen.  
  
3.  Wählen Sie das Zertifikat aus, mit dem Sie die Manifeste signieren möchten.  
  
4.  Zudem können Sie im Textfeld **Timestampserver-URL** die Adresse eines Timestampservers angeben. Dabei handelt es sich um einen Server, der einen Timestamp bereitstellt, mit dem angegeben wird, zu welchem Zeitpunkt das Manifest signiert wurde.  
  
### <a name="to-sign-application-and-deployment-manifests-using-an-existing-key-file"></a>So signieren Sie Anwendungs- und Bereitstellungsmanifeste mit einer vorhandenen Schlüsseldatei  
  
1.  Aktivieren Sie auf der Seite **Signierung** das Kontrollkästchen **ClickOnce-Manifeste signieren**.  
  
2.  Klicken Sie auf die Schaltfläche **Aus Datei wählen**.  
  
     Das Dialogfeld **Datei auswählen** wird angezeigt.  
  
3.  Suchen Sie im Dialogfeld **Datei auswählen** den Speicherort der zu verwendenden Schlüsseldatei (PFX-Datei), und klicken Sie dann auf **Öffnen**.  
  
    > [!NOTE]
    >  Diese Option kann nur bei Dateien mit der Erweiterung .pfx verwendet werden. Speichern Sie Schlüsseldateien oder Zertifikate in einem anderen Format im Windows-Zertifikatspeicher, und wählen Sie das Zertifikat aus, das im vorhergehenden Verfahren beschrieben wurde. Zu den Funktionen des ausgewählten Zertifikats sollten auch Codesignaturen gehören.  
  
     Das Dialogfeld **Kennwort zum Öffnen der Datei eingeben** wird angezeigt. (Wenn die PFX-Datei bereits im Windows-Zertifikatspeicher gespeichert oder nicht kennwortgeschützt ist, werden Sie zur Eingabe eines Kennworts aufgefordert.)  
  
4.  Geben Sie das Kennwort für den Zugriff auf die Schlüsseldatei ein, und drücken Sie die EINGABETASTE.  
  
### <a name="to-sign-application-and-deployment-manifests-using-a-test-certificate"></a>So signieren Sie Anwendungs- und Bereitstellungsmanifeste mit einem Testzertifikat  
  
1.  Aktivieren Sie auf der Seite **Signierung** das Kontrollkästchen **ClickOnce-Manifeste signieren**.  
  
2.  Klicken Sie zum Erstellen eines neuen Zertifikats zum Testen auf die Schaltfläche **Testzertifikat erstellen**.  
  
3.  Geben Sie im Dialogfeld **Testzertifikat erstellen** ein Kennwort ein, um das Testzertifikat zu schützen.  
  
## <a name="generating-unsigned-manifests"></a>Generieren von unsignierten Manifesten  
 Das Signieren der ClickOnce-Manifeste ist für EXE-basierte Anwendungen optional. In den folgenden Anleitungen wird dargestellt, wie unsignierte ClickOnce-Manifeste generiert werden.  
  
> [!IMPORTANT]
>  Unsignierte Manifeste können die Entwicklung und das Testen der Anwendung vereinfachen. Unsignierte Manifeste führen in einer Produktionsumgebung jedoch zu beträchtlichen Sicherheitsrisiken. Ziehen Sie die Verwendung unsignierter Manifeste nur in Betracht, wenn die ClickOnce-Anwendung auf Computern in einem Intranet ausgeführt wird, das vollständig vom Internet oder anderen Quellen bösartigen Codes abgeschirmt ist.  
  
 Standardmäßig werden durch ClickOnce automatisch signierte Manifeste generiert, sofern nicht mindestens eine Datei ausdrücklich aus dem generierten Hash ausgeschlossen wird. Wenn alle Dateien im Hash eingeschlossen sind, werden beim Veröffentlichen der Anwendung somit signierte Manifeste erstellt. Dies gilt auch, wenn das Kontrollkästchen **ClickOnce-Manifeste signieren** deaktiviert ist.  
  
#### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>So generieren Sie nicht signierte Manifeste und schließen alle Dateien in den generierten Hash ein  
  
1.  Zum Generieren nicht signierter Manifeste, die alle Dateien im Hash enthalten, müssen Sie die Anwendung zunächst mit signierten Manifesten veröffentlichen. Signieren Sie daher zunächst die ClickOnce-Manifeste, indem Sie eines der oben aufgeführten Verfahren ausführen, und veröffentlichen Sie dann die Anwendung.  
  
2.  Deaktivieren Sie auf der Seite **Signierung** das Kontrollkästchen **ClickOnce-Manifeste signieren**.  
  
3.  Setzen Sie die Veröffentlichungsversion zurück, damit nur eine Version der Anwendung verfügbar ist. Standardmäßig wird die Revisionsnummer der Veröffentlichungsversion von Visual Studio bei jedem Veröffentlichen einer Anwendung automatisch erhöht. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion](../deployment/how-to-set-the-clickonce-publish-version.md).  
  
4.  Veröffentlichen Sie die Anwendung.  
  
#### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>So generieren Sie nicht signierte Manifeste und schließen eine oder mehrere Dateien aus dem generierten Hash aus  
  
1.  Deaktivieren Sie auf der Seite **Signierung** das Kontrollkästchen **ClickOnce-Manifeste signieren**.  
  
2.  Öffnen Sie das Dialogfeld **Anwendungsdateien**, und legen Sie **Hash** für die Dateien auf **Ausschließen** fest, die Sie aus dem generierten Hash ausschließen möchten.  
  
    > [!NOTE]
    >  Durch Ausschließen einer Datei aus dem Hash wird ClickOnce so konfiguriert, dass das automatische Signieren von Manifesten deaktiviert wird. Daher muss nicht zuerst mit signierten Manifesten veröffentlicht werden, wie es im vorhergehenden Verfahren der Fall war.  
  
3.  Veröffentlichen Sie die Anwendung.  
  
## <a name="see-also"></a>Siehe auch  
 [Assemblys mit starkem Namen](/dotnet/framework/app-domains/strong-named-assemblies)   
 [Vorgehensweise: Erstellen eines öffentlichen/privaten Schlüsselpaars](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)   
 [Seite „Signierung“, Projekt-Designer](../ide/reference/signing-page-project-designer.md)   
 [ClickOnce-Sicherheit und Bereitstellung](../deployment/clickonce-security-and-deployment.md)
