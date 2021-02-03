---
title: Recursos de política de autosserviço
description: Um parceiro define políticas de autosserviço para um cliente.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 04daf6aaeb69153c4139941188f53dbab8979969
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/08/2020
ms.locfileid: "97768953"
---
# <a name="selfservepolicy-resource"></a><span data-ttu-id="398e3-103">Recurso SelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="398e3-103">SelfServePolicy resource</span></span>

<span data-ttu-id="398e3-104">**Aplica-se a:**</span><span class="sxs-lookup"><span data-stu-id="398e3-104">**Applies to:**</span></span>

- <span data-ttu-id="398e3-105">Partner Center</span><span class="sxs-lookup"><span data-stu-id="398e3-105">Partner Center</span></span>

<span data-ttu-id="398e3-106">Um parceiro define políticas de autosserviço para um cliente.</span><span class="sxs-lookup"><span data-stu-id="398e3-106">A partner sets self serve policies for a customer.</span></span>

## <a name="selfservepolicy"></a><span data-ttu-id="398e3-107">AutoServePolicy</span><span class="sxs-lookup"><span data-stu-id="398e3-107">SelfServePolicy</span></span>

<span data-ttu-id="398e3-108">Descreve um carrinho.</span><span class="sxs-lookup"><span data-stu-id="398e3-108">Describes a cart.</span></span>

| <span data-ttu-id="398e3-109">Propriedade</span><span class="sxs-lookup"><span data-stu-id="398e3-109">Property</span></span>              | <span data-ttu-id="398e3-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="398e3-110">Type</span></span>             | <span data-ttu-id="398e3-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e3-111">Description</span></span>                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="398e3-112">ID</span><span class="sxs-lookup"><span data-stu-id="398e3-112">id</span></span>                    | <span data-ttu-id="398e3-113">string</span><span class="sxs-lookup"><span data-stu-id="398e3-113">string</span></span>           | <span data-ttu-id="398e3-114">Um identificador de política de autosserviço que é fornecido após a criação bem sucedida da política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="398e3-114">A self serve policy identifier that is supplied upon successful creation of the self serve policy.</span></span>     |
| <span data-ttu-id="398e3-115">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="398e3-115">SelfServeEntity</span></span>       | <span data-ttu-id="398e3-116">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="398e3-116">SelfServeEntity</span></span>  | <span data-ttu-id="398e3-117">A entidade self-serve a quem está a ser concedido acesso.</span><span class="sxs-lookup"><span data-stu-id="398e3-117">The self serve entity that is being granted access.</span></span>                                                     |
| <span data-ttu-id="398e3-118">Grantor</span><span class="sxs-lookup"><span data-stu-id="398e3-118">Grantor</span></span>               | <span data-ttu-id="398e3-119">Grantor</span><span class="sxs-lookup"><span data-stu-id="398e3-119">Grantor</span></span>          | <span data-ttu-id="398e3-120">O concededor que está a conceder acesso.</span><span class="sxs-lookup"><span data-stu-id="398e3-120">The grantor that is granting access.</span></span>                                                                    |
| <span data-ttu-id="398e3-121">Permissões</span><span class="sxs-lookup"><span data-stu-id="398e3-121">Permissions</span></span>           | <span data-ttu-id="398e3-122">Matriz de Permissão</span><span class="sxs-lookup"><span data-stu-id="398e3-122">Array of Permission</span></span>| <span data-ttu-id="398e3-123">Um conjunto de recursos [de permissão.](#permission)</span><span class="sxs-lookup"><span data-stu-id="398e3-123">An Array of [Permission](#permission) resources.</span></span>                                                                     |

## <a name="selfserveentity"></a><span data-ttu-id="398e3-124">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="398e3-124">SelfServeEntity</span></span>

<span data-ttu-id="398e3-125">Representa a entidade que recebe permissões.</span><span class="sxs-lookup"><span data-stu-id="398e3-125">Represents the entity being granted permissions.</span></span>

| <span data-ttu-id="398e3-126">Propriedade</span><span class="sxs-lookup"><span data-stu-id="398e3-126">Property</span></span>             | <span data-ttu-id="398e3-127">Tipo</span><span class="sxs-lookup"><span data-stu-id="398e3-127">Type</span></span>|<span data-ttu-id="398e3-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e3-128">Description</span></span>|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="398e3-129">SelfServeEntityType</span><span class="sxs-lookup"><span data-stu-id="398e3-129">SelfServeEntityType</span></span>  | <span data-ttu-id="398e3-130">string</span><span class="sxs-lookup"><span data-stu-id="398e3-130">string</span></span>                           | <span data-ttu-id="398e3-131">A entidade a quem foi concedido acesso, valores aceites: Cliente.</span><span class="sxs-lookup"><span data-stu-id="398e3-131">The entity being granted access, accepted values: Customer.</span></span>                                 |
| <span data-ttu-id="398e3-132">TenantID</span><span class="sxs-lookup"><span data-stu-id="398e3-132">TenantID</span></span>             | <span data-ttu-id="398e3-133">string</span><span class="sxs-lookup"><span data-stu-id="398e3-133">string</span></span>                           | <span data-ttu-id="398e3-134">O identificador de inquilino da entidade que tem acesso.</span><span class="sxs-lookup"><span data-stu-id="398e3-134">The tenant identifier of the entity being granted access.</span></span>                                   |

## <a name="grantor"></a><span data-ttu-id="398e3-135">Grantor</span><span class="sxs-lookup"><span data-stu-id="398e3-135">Grantor</span></span>

<span data-ttu-id="398e3-136">Representa o concededor que concede as permissões.</span><span class="sxs-lookup"><span data-stu-id="398e3-136">Represents the grantor granting the permissions.</span></span>

| <span data-ttu-id="398e3-137">Propriedade</span><span class="sxs-lookup"><span data-stu-id="398e3-137">Property</span></span>             | <span data-ttu-id="398e3-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="398e3-138">Type</span></span>|<span data-ttu-id="398e3-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e3-139">Description</span></span>|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="398e3-140">GrantorType</span><span class="sxs-lookup"><span data-stu-id="398e3-140">GrantorType</span></span>          | <span data-ttu-id="398e3-141">string</span><span class="sxs-lookup"><span data-stu-id="398e3-141">string</span></span>                           | <span data-ttu-id="398e3-142">O bolseiro que concede acesso, valores aceites: BillToPartner.</span><span class="sxs-lookup"><span data-stu-id="398e3-142">The grantor granting access, accepted values: BillToPartner.</span></span>                               |
| <span data-ttu-id="398e3-143">TenantID</span><span class="sxs-lookup"><span data-stu-id="398e3-143">TenantID</span></span>             | <span data-ttu-id="398e3-144">string</span><span class="sxs-lookup"><span data-stu-id="398e3-144">string</span></span>                           | <span data-ttu-id="398e3-145">O identificador de inquilino da entidade que concede acesso.</span><span class="sxs-lookup"><span data-stu-id="398e3-145">The tenant identifier of the entity granting access.</span></span>                                       |


## <a name="permission"></a><span data-ttu-id="398e3-146">Permissão</span><span class="sxs-lookup"><span data-stu-id="398e3-146">Permission</span></span>

<span data-ttu-id="398e3-147">Representa uma permissão na política de autosserviço.</span><span class="sxs-lookup"><span data-stu-id="398e3-147">Represents a permission in the self serve policy.</span></span>

| <span data-ttu-id="398e3-148">Propriedade</span><span class="sxs-lookup"><span data-stu-id="398e3-148">Property</span></span>             | <span data-ttu-id="398e3-149">Tipo</span><span class="sxs-lookup"><span data-stu-id="398e3-149">Type</span></span>|<span data-ttu-id="398e3-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e3-150">Description</span></span>|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="398e3-151">Recurso</span><span class="sxs-lookup"><span data-stu-id="398e3-151">Resource</span></span>             | <span data-ttu-id="398e3-152">string</span><span class="sxs-lookup"><span data-stu-id="398e3-152">string</span></span>                           | <span data-ttu-id="398e3-153">O acesso ao recurso também está a ser concedido: AzureReservedInstances.</span><span class="sxs-lookup"><span data-stu-id="398e3-153">The resource access is being granted too: AzureReservedInstances.</span></span>                          |
| <span data-ttu-id="398e3-154">Ação</span><span class="sxs-lookup"><span data-stu-id="398e3-154">Action</span></span>               | <span data-ttu-id="398e3-155">string</span><span class="sxs-lookup"><span data-stu-id="398e3-155">string</span></span>                           | <span data-ttu-id="398e3-156">O acesso à ação está a ser concedido para: Compra</span><span class="sxs-lookup"><span data-stu-id="398e3-156">The action access is being granted for: Purchase</span></span>                                           |
