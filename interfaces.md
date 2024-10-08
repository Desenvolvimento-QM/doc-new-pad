
# Interfaces da API

## `iTableReadParams`
Parâmetros para leitura de usuários:
```typescript
export interface iTableReadParams {
    email?: string;
    emailVerified?: boolean;
    enabled?: boolean;
    exact?: boolean;
    first?: string;
    max?: string;
    firstName?: string;
    lastName?: string;
    q?: string;
    search?: string;
    username?: string;
}
```

## `CreateUserDto`
Estrutura para criação de usuários:
```typescript
export interface CreateUserDto {
    username: string;
    enabled: boolean;
    emailVerified: boolean;
    updatePassword: boolean;
    firstName: string;
    lastName: string;
    email: string;
    phoneNumber?: string;
    locale: 'pt-BR' | 'en' | 'es';
    default_role: iRealmRolesOptions | '-';
}
```

## `UpdateUserDto`
Estrutura para atualização de usuários, estendendo `CreateUserDto`:
```typescript
export interface UpdateUserDto extends CreateUserDto {
    id: string;
}
```

## `iUserData`
Dados de um usuário:
```typescript
export interface iUserData {
    id: string;
    firstName: string;
    lastName: string;
    username: string;
    name: string;
    email: string;
    emailVerified: boolean;
    enabled: boolean;
    created: string;
    requiredActions: string[];
    temporary_password?: string;
    phoneNumber?: string;
    app_resource_roles?: any[];
    creator_username?: string;
    creator_email?: string;
    creator_sub?: string;
    creator_name?: string;
    locale?: 'pt-BR' | 'en' | 'es';
    app_realm_role?: iRealmRolesOptions;
}
```

## `iRealmRolesOptions`
Opções de papéis de usuário no sistema:
```typescript
export const realm_roles_options = [
    { label: 'Administrador', value: 'admin', description: 'O papel de administrador tem acesso total ao sistema.', show: 'SHOW_ADMIN_ROLE' },
    { label: 'Contribuidor', value: 'contributor', description: 'O papel de contribuidor tem acesso limitado ao sistema.', show: 'SHOW_CONTRIBUTOR_ROLE' },
    { label: 'Leitor', value: 'reader', description: 'O papel de leitor tem acesso somente para leitura, para recursos não administrativos.', show: 'SHOW_READER_ROLE' },
    { label: 'Não autorizado', value: '-', description: 'O papel de não autorizado não tem acesso a nada, o usuário não pode fazer nenhuma ação.', show: 'SHOW_UNAUTHORIZED_ROLE' },
] as const;
```
