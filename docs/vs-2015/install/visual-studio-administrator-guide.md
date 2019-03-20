---
title: Administratorhandbuch für Visual Studio | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
caps.latest.revision: 76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 839573b296d01d10e3f4c06e94cb1553380c673c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "57868881"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio Administrator Guide
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation für Visual Studio 2017 finden Sie unter den [Administratorhandbuch für Visual Studio 2017](/visualstudio/install/visual-studio-administrator-guide).

Sie können Visual Studio 2015 in einem Netzwerk bereitstellen, solange jeder Zielcomputer erfüllt die [minimalen Installationsanforderungen](https://visualstudio.microsoft.com/vs/older-downloads/). Sie können eine Netzwerkfreigabe erstellen, indem Sie die Installationsdatei mit der Option „/layout“ ausführen (wie auf der Seite [Erstellen einer Offlineinstallation von Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md) beschrieben) und sie dann vom lokalen Computer auf die Netzwerkfreigabe kopieren. Wenn Sie ein ISO-Image verwenden, können Sie das ISO-Image bereitstellen und freigeben oder der ISO-Datei in eine Netzwerkfreigabe kopieren.  
  
 Beachten Sie, dass sich Installationen über eine Netzwerkfreigabe den ursprünglichen Quellspeicherort "merken". Dies bedeutet, dass Sie zur Reparatur eines Clients möglicherweise zur Netzwerkfreigabe zurückkehren müssen, über die der Client ursprünglich installiert wurde. Wählen Sie die Netzwerkadresse sorgfältig aus, sodass sie der Lebensdauer der Visual Studio 2015-Clients in Ihrer Organisation entspricht.  
  
## <a name="detection-and-servicing-keys"></a>Erkennungs- und Wartungsschlüssel  
 Mit den Erkennungsunterschlüsseln in der Registrierung können Sie ermitteln, ob bereits ein Visual Studio-Produkt auf einem Computer installiert ist. Sie können mithilfe dieser Erkennungsschlüssel in einer automatisierten Bereitstellung bestimmen, ob es erforderlich ist, mit einer Installation fortzufahren.  Finden Sie unter [Ermitteln von Systemanforderungen](../extensibility/internals/detecting-system-requirements.md)[Ermitteln von Systemanforderungen].  
  
## <a name="avoiding-reboots"></a>Vermeiden von Neustarts  
 Sie können Neustarts reduzieren, indem Sie vor der Bereitstellung von Visual Studio sicherstellen, dass alle Voraussetzungen für Visual Studio erfüllt sind. Für die .NET Framework verwenden müssen Sie die Computer neu starten, die Windows 8 ausgeführt werden, wenn Sie Visual Studio 2015 darauf bereitstellen, ohne die erste Installation von .NET Framework 4.6.  
  
 Für eine Windows- und Android-Geräteemulation müssen Sie möglicherweise Computer neu starten, wenn die Windows-Funktion "Hyper-V" noch nicht aktiviert ist. Bei der Webbereitstellung müssen Sie möglicherweise Computer neu starten, wenn die Windows-Funktion "Webserver" noch nicht aktiviert wurde. Bei der Office-Bereitstellung müssen Sie möglicherweise Computer neu starten, wenn die Windows-Funktion "Windows Identify Foundation" noch nicht aktiviert wurde. Starten Sie Computer neu, wenn die Windows-Funktion „Webserver“ noch nicht aktiviert wurde. Bei der Office-Bereitstellung müssen Sie möglicherweise Computer neu starten, wenn die Windows-Funktion "Windows Identify Foundation" noch nicht aktiviert wurde. Weitere Informationen zum Automatisieren der Erkennung und Installation von Windows-Funktionen finden Sie unter [Installing a server role on a server running a Server Core installation of Windows Server 2008 R2](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx)(Installieren einer Serverrolle auf einem Server mit einer Server Core-Installation von Windows Server 2008 R2) (in englischer Sprache).  
  
## <a name="error-return-codes"></a>Fehlerrückgabecodes  
 In der folgenden Tabelle sind wichtige Fehlercodes aufgeführt. Sie können mithilfe dieser Fehlercodes innerhalb Ihrer Automatisierung entscheiden, ob ein Neustart erforderlich ist und ob die Installation erfolgreich war. Wenn Sie einen Fehlercode erhalten, sollten Sie die Schritte zur Problembehandlung auf die [Installieren von Visual Studio](../install/install-visual-studio-2015.md) Seite.  
  
|Setup-Status|Neustart nicht erforderlich|Neustart erforderlich|Beschreibung|  
|------------------|--------------------------|----------------------|-----------------|  
|Erfolgreich|0x00000000 [0]|0x00000bc2 [3010]|Erfolgreiche Installation.|  
|Block|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|Wenn als einziger Block "Reboot Pending" gemeldet wird, ist der zurückgegebene Wert "Incomplete-Reboot Required" (0x80048bc7).|  
|Abbrechen|0x00000642 [1602]|0x80048642 [-2147187134]|Wenn der Reboot-Wert zurückgegeben wird, ist der Rückgabecode "1602".|  
|Unvollständig-Neustart erforderlich|Nicht zutreffend|0x80048bc7 [-2147185721]|Vor dem Fortsetzen der Installation muss der Computer neu gestartet werden.|  
|Fehler|0x00000643 [1603]|0x80048643 [-2147187133]|Wenn der Reboot-Wert zurückgegeben wird, ist der Rückgabecode "1603".|  
  
## <a name="interactive-administrator-installer"></a>Interaktiver Installer für den Administrator  
 Wenn Sie einen interaktiven Installer auf die Visual Studio-Installation aufsetzen, können Sie den Fortschritt über den Visual Studio-Installer verfolgen. Der Installer für Visual Studio 2015 basiert auf der Open Source-WiX-Chainer-Technologie (Windows Installer XML), auch bekannt als „burn“. Die burn-Technologie unterstützt zwei Kommunikationsprotokolle: burn und netfx4. Eine kurze Referenz finden Sie in der Beschreibung des Protocol-Attributs in der Dokumentation für das ExePackage-Element unter [wixtoolset.org](http://wixtoolset.org/). Für die Integration ist möglicherweise eine Prüfung der WiX-Open Source-Implementierung des Protocol-Attributs erforderlich.  
  
## <a name="controlling-what-is-installed"></a>Steuern der installierten Elemente  
 Wenn Sie steuern möchten, welche Elemente Ihre Endbenutzer installieren können, haben Sie zwei Optionen: die Installation über die Administratordatei und die Befehlszeilenoptionen. Wählen Sie die Installation über die Administratordatei, wenn Sie beschränken möchten, welche Elemente Ihre Endbenutzer bei der Visual Studio-Installation auswählen können. Wählen Sie die Befehlszeilenparameter aus, wenn Sie eine anfängliche Konfiguration erstellen, aber Ihren Endbenutzern erlauben möchten, die Optionen für die Visual Studio-Installation selbst festzulegen.  
  
 Weitere Informationen zur Funktion der Administratordatei finden Sie unter [How to: Create and Run an Unattended Installation of Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) und [How to: Automatically apply product keys when deploying Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).  Weitere Informationen zu den Befehlszeilenoptionen finden Sie unter den [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) Seite.  
  
## <a name="specifying-customer-feedback-settings"></a>Festlegen von Kundenfeedbackeinstellungen  
 Standardmäßig ermöglicht die Visual Studio-Installation Kundenfeedback. Sie können Visual Studio so konfigurieren, dass Kundenfeedback auf einzelnen Computern deaktiviert wird. Ändern Sie dazu den Wert des folgenden Registrierungsschlüssels in die Zeichenfolge „0“.  
  
 **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  
**OptIn**  
  
 (Ändern Sie ihn beispielsweise in HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM OptIn="0")  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Gewusst wie: Installieren eines bestimmten Releases von Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md)|Beschreibt, wie Sie bestimmte Konfigurationen für die aktuelle Version von installieren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Gewusst wie: Erstellen und Ausführen einer unbeaufsichtigten Installation von Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|Beschreibt, wie Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] im unbeaufsichtigten Modus.|  
|[Gewusst wie: Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|Beschreibt, wie Produktschlüssel anwenden, wenn Sie auf mehreren Computern bereitstellen.|  
|[Help Viewer-Administratorhandbuch](../ide/help-viewer-administrator-guide.md)|Enthält Informationen dazu, wie Sie die lokale Hilfe Installationen netzwerkumgebungen zu verwalten, die oder haben keinen Zugriff auf das Internet.|  
|[Installieren von Visual Studio](../install/install-visual-studio-2015.md)|Enthält Anweisungen und Links zu Themen, die beschreiben, wie Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|