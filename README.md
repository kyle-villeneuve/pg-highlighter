# SQL Template Literal Syntax Highlighting

This VSCode plugin provides syntax highlighting for SQL template literals in TypeScript/JavaScript files. It recognizes SQL queries written using tagged template literals and applies appropriate syntax coloring.

## Supported Tags

The following template literal tags are recognized:

- `sql(client)`
- `sql<T>(client)`
- `sql`
- `sqlFragment`
- `select`
- `where`
- `joinAnd`
- `join`
- `groupBy`
- `orderBy`

## Usage Examples

```typescript
// Basic usage
sql`SELECT * FROM users`;

// With type parameters
sql<User>`SELECT * FROM users`;

// With object property access
builder.sql`SELECT * FROM users`;

// Other supported tags
builder.select`id, name FROM users`;
builder.where`age > 18`;
builder.join`LEFT JOIN orders ON users.id = orders.user_id`;
builder.orderBy`field DESC`;
```

## Syntax Highlighting Rules

### Template Tag Recognition

The plugin identifies SQL template literals using the following pattern:

1. Optional object reference: `[_$[:alpha:]][_$[:alnum:]]*`
   - Matches valid JavaScript identifier patterns
2. Template tag name: One of the supported tags listed above
   - Can include function-style syntax: `sql(paramName)`
3. Optional generic parameters: `<type>`
   - Supports full TypeScript type syntax
   - Highlighted according to TypeScript type rules

### SQL Content Highlighting

Within the template literal (between backticks), the following syntax is highlighted:

1. Comparison Operators

   - Matches: `>=`, `<=`, `!=`, `=`, `>`, `<`
   - Must be followed by either:
     - A dollar sign (`$`)
     - A word character or quote (`[\\w']`)
   - Highlighted as regular expressions

2. PostgreSQL Specific Syntax

   - Includes full PostgreSQL PL/pgSQL syntax highlighting

3. Template Interpolations

   - Standard JavaScript template literal substitutions (`${expression}`)
   - Highlighted according to TypeScript rules

4. Standard SQL Syntax
   - Includes general SQL syntax highlighting
   - Keywords, functions, types, and other SQL elements

## Technical Details

### Scope Names

- Main scope: `inline.tagged-template-sql`
- Template string: `string.template.ts`
- Embedded SQL: `meta.embedded.block.sql`
- Template delimiters: `punctuation.definition.string.template.begin/end.js`
- Comparison operators: `string.regexp.sql`

### Injection Rules

The syntax highlighting is injected into:

- TypeScript/JavaScript source code
- Excludes comments and string literals
- Only applies to the specified template tags

### Inheritance

The plugin inherits syntax highlighting rules from:

- TypeScript (`source.ts`)
- PostgreSQL (`source.plpgsql.postgres`)
- Standard SQL (`source.sql`)

This ensures consistent highlighting with the base language features while adding SQL-specific enhancements.
