# KDocs Multi-Dimensional Table Schema

## Table Information

- **File ID**: `ciLdfAcM6jjU`
- **File URL**: https://www.kdocs.cn/l/ciLdfAcM6jjU
- **Sheet ID**: `1`
- **Sheet Name**: 数据表

## Field Definitions

| Field ID | Field Name    | Type          | Format        | Description  |
|----------|--------------|---------------|---------------|--------------|
| B        | 文章标题      | MultiLineText | -             | Article title |
| C        | 链接          | Url           | -             | Article URL   |
| D        | 摘要          | MultiLineText | -             | Article summary (max 200 chars) |
| E        | 关键字标签     | MultiLineText | -             | Keyword tags (1-5, comma-separated) |
| F        | 文章发布日期   | Date          | yyyy/MM/dd    | Article publish date (Unix timestamp in ms) |
| H        | 作者          | MultiLineText | -             | Article author |

## Date Field Format

The `文章发布日期` field uses the `Date` type. When creating records via `mcp__kdocs__dbsheet.create_records`, the date value must be a **Unix timestamp in milliseconds** (integer).

Example: `2025-01-15` → `1736899200000`

To convert a date string to Unix timestamp in milliseconds, use:
```bash
date -d "2025-01-15" +%s000
```

## Creating Records

Use `mcp__kdocs__dbsheet.create_records` with the following parameters:

```json
{
  "file_id": "ciLdfAcM6jjU",
  "sheet_id": 1,
  "records": [
    {
      "fields": {
        "文章标题": "Example Title",
        "链接": "https://example.com/article",
        "摘要": "This is a summary...",
        "关键字标签": "AI,technology,innovation",
        "文章发布日期": 1736899200000,
        "作者": "John Doe"
      }
    }
  ]
}
```

## URL Field Format

The `链接` field is of type `Url`. When writing a URL value, pass the URL string directly. The KDocs API handles the linking and display text automatically.
