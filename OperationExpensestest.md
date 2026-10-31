package co.edu.unillanos.msg.domain;


import java.math.BigDecimal;
import java.math.RoundingMode;
import java.util.Objects;


/**
 * Gastos operativos anuales estimados de la MSG Foundation.
 * Rol responsable: Inversiones.
 */
public final class OperatingExpenses {


    private static final BigDecimal WEEKS_PER_YEAR = new BigDecimal("52");


    private final BigDecimal annualAmount;


    public OperatingExpenses(BigDecimal annualAmount) {
        this.annualAmount = Objects.requireNonNull(annualAmount);
    }


    public BigDecimal annualAmount() {
        return annualAmount;
    }


    /** RN7: gasto anual repartido igual entre 52 semanas, con 2 decimales. */
    public BigDecimal weeklyAmount() {
        return annualAmount.divide(WEEKS_PER_YEAR, 2, RoundingMode.HALF_EVEN);
    }
}
