
```
#自带数据，可查看数据格式
expr = readRDS(paste0(system.file(package = "ComplexHeatmap"), "/extdata/gene_expression.rds"))

mat = as.matrix(expr[, grep("cell", colnames(expr))])

type = gsub("s\\d+_", "", colnames(mat))

ha = HeatmapAnnotation(df = data.frame(type = type))

Heatmap(mat, name = "expression", km = 5, top_annotation = ha, top_annotation_height = unit(4, "mm"),

show_row_names = FALSE, show_column_names = FALSE) +

Heatmap(expr$length, name = "length", width = unit(5, "mm"), col = colorRamp2(c(0, 100000), c("white", "orange"))) +

Heatmap(expr$type, name = "type", width = unit(5, "mm")) +

Heatmap(expr$chr, name = "chr", width = unit(5, "mm"), col = rand_color(length(unique(expr$chr))))
```


版权声明：本文为CSDN博主 [R语言中文社区](https://blog.csdn.net/kMD8d5R/article/details/81008892) 的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
