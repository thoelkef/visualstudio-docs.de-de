---
title: Synchronisieren der Einstellungen in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/23/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 10
author: kempb
ms.author: kempb
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
translationtype: Human Translation
ms.sourcegitcommit: 4166ed8bfa0234e1cc453bd045974b412f87ae42
ms.openlocfilehash: a1a310aa6bf0e3d0042f35f5c49612f33b89fb61
ms.lasthandoff: 02/22/2017

---
# <a name="synchronize-your-settings-in-visual-studio"></a>Synchronisieren der Einstellungen in Visual Studio
Wenn Sie sich auf mehreren Computern mit demselben Personalisierungskonto bei Visual Studio anmelden, werden Ihre Einstellungen standardmäßig auf allen Computern synchronisiert.

## <a name="synchronized-settings"></a>Synchronisierte Einstellungen  
 Standardmäßig werden die folgenden Einstellungen synchronisiert:  

-   Entwicklungseinstellungen (Sie müssen eine Reihe von Einstellungen auswählen, wenn Sie Visual Studio zum ersten Mal ausführen; die Auswahl kann jedoch jederzeit geändert werden. Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio (Anpassen der Entwicklungseinstellungen in Visual Studio)](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).)  

-   Im Folgenden finden Sie die Optionen auf den Seiten **Tools &#124; Optionen**:  

    -   **Design** und Menüleisten-Schreibweiseneinstellungen auf der Optionsseite **Umgebung** > **Allgemein**  

    -   Alle Einstellungen auf der Optionsseite **Umgebung** > **Schriftarten und Farben**  

    -   Alle Tastenkombinationen auf der Optionsseite **Umgebung** > **Tastatur**  

    -   Alle Einstellungen auf der Optionsseite **Umgebung, Registerkarten und Fenster**  

    -   Alle Einstellungen auf der Optionsseite **Umgebung** > **Start**  

    -   Alle Einstellungen auf den Optionsseiten des **Text-Editors**  

-   Alle Einstellungen auf den Optionsseiten für den XAML-Designer  

-   Benutzerdefinierte Befehlsaliase. Weitere Informationen zur Definition von Befehlsaliasen finden Sie unter [Visual Studio-Befehlsaliase](../ide/reference/visual-studio-command-aliases.md).  

-   Benutzerdefinierte Fensterlayouts auf der Seite **Fenster &#124; Fensterlayouts verwalten**  

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Deaktivieren der synchronisierten Einstellungen auf einem bestimmten Computer  
 Die synchronisierten Einstellungen für Visual Studio sind standardmäßig aktiviert. Sie können die synchronisierten Einstellungen auf einem Computer deaktivieren, indem Sie zur Seite **Tools &#124; Optionen &#124; Umgebung &#124; Synchronisierte Einstellungen** wechseln und das Kontrollkästchen deaktivieren.  Angenommen, Sie möchten, dass die Einstellungen von Visual Studio auf Computer A nicht synchronisiert werden. So werden alle auf Computer A vorgenommenen Änderungen weder auf Computer B noch auf Computer C angezeigt. Computer B und Computer C nehmen weiterhin eine Synchronisierung miteinander vor, jedoch nicht mit Computer A.  

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchronisieren von Einstellungen mit allen Produkten und Editionen der Visual Studio-Familie  
 Einstellungen können mit allen Editionen von Visual Studio synchronisiert werden, einschließlich der Edition Community. Einstellungen werden auch mit allen Produkten der Visual Studio-Familie synchronisiert. Jedes dieser Familienprodukte weist jedoch möglicherweise eigene Einstellungen auf, die nicht für Visual Studio freigegeben werden. Beispielsweise werden für ein Produkt spezifische Einstellungen auf Computer A für ein anderes Produkt auf Computer B freigegeben, jedoch nicht für Visual Studio auf Computer A oder B.  

## <a name="see-also"></a>Siehe auch  
 [Personalisieren der IDE](../ide/personalizing-the-visual-studio-ide.md)

