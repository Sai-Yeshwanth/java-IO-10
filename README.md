import java.io.FileInputStream;  
import java.io.IOException;  
import org.apache.poi.*;  
public class Jala {
	public static void main(String[] args) throws IOException {

		FileInputStream fis = new FileInputStream(new File("C:\\demo\\student.xls"));
		HSSFWorkbook wb = new HSSFWorkbook(fis);
		HSSFSheet sheet = wb.getSheetAt(0);
		FormulaEvaluator formulaEvaluator = wb.getCreationHelper().createFormulaEvaluator();
		for (Row row : sheet) {
			for (Cell cell : row) {
				switch (formulaEvaluator.evaluateInCell(cell).getCellType()) {
				case Cell.CELL_TYPE_NUMERIC:
					System.out.print(cell.getNumericCellValue() + "\t");
					break;
				case Cell.CELL_TYPE_STRING:
					System.out.print(cell.getStringCellValue() + "\t");
					break;
				}
			}
			System.out.println();
		}
	}
}
