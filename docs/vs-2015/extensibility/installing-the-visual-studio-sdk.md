---
title: Installieren des Visual Studio SDK | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88a6266a3f5910def0bf5041a37f89c2b3d67416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842331"
---
# <a name="installing-the-visual-studio-sdk"></a>Installieren des Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installieren des Visual Studio SDK als Teil einer Visual Studio-Installation  
 Wenn Sie das VSSDK in die Visual Studio-Installation einschließen möchten, müssen Sie eine benutzerdefinierte Installation durchführen.  
  
> [!NOTE]
> In der ausführbaren Installationsdatei wird das Visual Studio SDK **Visual Studio-Erweiterungstools**aufgerufen.  
  
1. Starten Sie die Installation von Visual Studio 2015. Sie können eine beliebige Edition von Visual Studio mit Ausnahme von Express installieren.  
  
2. Wählen Sie auf dem ersten Bildschirm **Benutzer**definiert und nicht **Standard**aus. Klicken Sie auf **Weiter**.  
  
3. Eine Strukturansicht der benutzerdefinierten Features sollte angezeigt werden. Öffnen Sie **gängige Tools**. **Visual Studio-Erweiterungstools** sollte angezeigt werden.  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. Aktivieren Sie **Visual Studio-Erweiterungstools** , und klicken Sie **dann auf weiter** .  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Installieren von Visual Studio SDK nach der Installation von Visual Studio  
 Wenn Sie nach Abschluss der Visual Studio-Installation das Visual Studio SDK installieren möchten, führen Sie die folgenden Schritte aus:  
  
1. Wechseln Sie zu **Systemsteuerung**> Programme > Programme > Funktionen und suchen Sie nach **Visual Studio 2015**. Sie können das Visual Studio SDK für eine beliebige Edition von Visual Studio 2015 mit Ausnahme von Express installieren.  
  
2. Klicken Sie mit der rechten Maustaste auf **Visual Studio 2015**, und klicken Sie dann auf **ändern**. Die Seite Installation sollte angezeigt werden.  
  
3. Befolgen Sie die gleiche Vorgehensweise wie bei der **Installation des Visual Studio SDK als Teil einer Visual Studio-Installation** .  
  
4. Klicken Sie auf den **Visual Studio-Erweiterungstools** Link, um das Visual Studio SDK zu installieren.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Installieren des Visual Studio SDK aus einer Projekt Mappe  
 Wenn Sie eine Projekt Mappe mit einem Erweiterbarkeits Projekt öffnen, ohne zuvor das VSSDK zu installieren, werden Sie über den Projektmappen-Explorer über eine hervorgehobene Informationsleiste aufgefordert. Das Ergebnis sollte etwa wie folgt aussehen:  
  
 ![Solutionexplorerinstall](../extensibility/media/solutionexplorerinstall.png "Solutionexplorerinstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Installieren des Visual Studio SDK über die Befehlszeile  
 Sie können das VSSDK über die Befehlszeile installieren, indem Sie den **/InstallSelectableItems** -Schalter mit dem Visual Studio-Installer verwenden. Ausführliche Informationen zur Verwendung von Befehlszeilen Parametern mit dem Installationsprogramm finden Sie unter [Installieren von Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Im folgenden wird erläutert, wie Sie das VSSDK mithilfe des Visual Studio 2015 Community-Installers automatisch installieren:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Beachten Sie, dass Sie das Visual Studio-Installationsprogramm verwenden müssen, der mit der installierten Version von Visual Studio übereinstimmt. Wenn Sie z. B. Visual Studio Enterprise auf dem Computer installiert haben, müssen Sie das Visual Studio Enterprise-Installationsprogramm (vs_enterprise.exe) ausführen.
