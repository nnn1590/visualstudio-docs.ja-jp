---
title: SolutionFolder 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4fd2ce948a3e18633f4c9875fa3ec0b064a91b35
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331988"
---
# <a name="solutionfolder-element-visual-studio-templates"></a>SolutionFolder 要素 (Visual Studio テンプレート)
複数プロジェクトのテンプレートをグループ化します。

 \<VSTemplate> \<TemplateContent> \<ProjectCollection> \<SolutionFolder>

## <a name="syntax"></a>構文

```
<SolutionFolder Name="DirectoryName">
    ...
</SolutionFolder>
```

## <a name="attributes-and-elements"></a>属性および要素
 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`Name`|必須の属性です。<br /><br /> ソリューション フォルダーの名前。|

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|省略可能な要素です。<br /><br /> 複数プロジェクトのテンプレートにある プロジェクトの .vstemplate ファイル パスを指定します。|
|`SolutionFolder`|省略可能な要素です。<br /><br /> 複数プロジェクトのテンプレートをグループ化します。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|複数プロジェクトのテンプレートの構成と内容を指定します。|
|`SolutionFolder`|複数プロジェクトのテンプレートをグループ化します。|

## <a name="remarks"></a>Remarks
 複数プロジェクトのテンプレートは、2 つ以上のプロジェクトのコンテナーとして機能します。 `SolutionFolder` 要素は、テンプレート内のプロジェクトをグループに編成するために使用されます。 `SolutionFolder` 要素で指定されたフォルダーは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内のプロジェクトのソリューション フォルダーとして作成されます。 複数プロジェクトのテンプレートの詳細については、次を参照してください。[方法。複数のプロジェクト テンプレートを作成する](../ide/how-to-create-multi-project-templates.md)します。

## <a name="example"></a>例
 この例では、`SolutionFolder` 要素を使用して、複数のプロジェクトのテンプレートを 2 つのグループ、`Math Classes` と `Graphics Classes` に分割します。 テンプレートには 4 つのプロジェクトが含まれ、その 2 つは各ソリューション フォルダーに配置されます。

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>関連項目
- [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)
- [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)
- [方法: 複数プロジェクトのテンプレートを作成する](../ide/how-to-create-multi-project-templates.md)