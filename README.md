## Sequelize Transactional Decorator

- this is simple package that provide you with a roubust out of the box @Transactional for sequelize

---

### how to use it:

- frist you have to call initializeSequelizeWithTransactionalContext in your bootstrap flow.

NOTE: for nestjs, it must be called before nest app creation.

```tsx
await initializeSequelizeWithTransactionalContext({
      dialect,
      host,
      port,
      username,
      password,
      database,
      models: ...Model,
    });
```

- for nestjs: import **SequelizeModule** and add it to your DatabaseModule Like the following**:**
  ```tsx
  @Global()
  @Module({
    imports: [SequelizeModule],
    providers: [...repositories],
    exports: [...repositories],
  })
  export class DatabaseModule {}
  ```

---

### Usage Example:

```tsx
  @Transactional({
    isolationLevel: 'READ COMMITTED',
  })
  async createPost(fails: boolean = false): Promise<Post> {
    return await this.testTransactionIsolated(fails);
  }
```

---

Made With ❤️ @Baianat
