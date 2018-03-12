---
title: "InstallVSTemplates-Schalter „devenv.exe“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /InstallVSTemplates switch
- /InstallVSTemplates Devenv switch
- InstallVSTemplates switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 529979caa801ace8dd649cf1614f2eeb27ca070b
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="installvstemplates-devenvexe"></a>/InstallVSTemplates (devenv.exe)

Der /InstallVSTemplates-Schalter registriert unter „*\<Visual Studio-Installationspfad>*\Common7\IDE\ProjectTemplates\“ oder „*\<Visual Studio-Installationspfad>*\Common7\IDE\ItemTemplates\“ gespeicherte Projekt- oder Elementvorlagen, damit in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** darauf zugegriffen werden kann.

> [!WARNING]
> Dieser Schalter wird nur für Visual Studio-Partnerentwicklung unterstützt. Sie müssen „devenv“ als Administrator ausführen, um die Schalter [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) und [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) verwenden zu können. Weitere Informationen finden Sie unter [Benutzerberechtigungen](../../ide/user-permissions-and-visual-studio.md).

## <a name="syntax"></a>Syntax

```
devenv.exe /InstallVSTemplates
```

## <a name="see-also"></a>Siehe auch

[Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)