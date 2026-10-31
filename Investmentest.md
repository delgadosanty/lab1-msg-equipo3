package co.edu.unillanos.msg.domain;


import java.math.BigDecimal;
import java.math.RoundingMode;
import java.util.Objects;


/**
 * Inversión de la MSG Foundation.
 * Rol responsable: Inversiones.
 *
 * Decisión D3 (tomada, revisable): la clase está declarada final.
 */
public final class Investment {


    private static final BigDecimal WEEKS_PER_YEAR = new BigDecimal("52");


    private final String investmentId;
    private final String description;
    private final BigDecimal annualExpectedReturn;


    public Investment(String investmentId, String description, BigDecimal annualExpectedReturn) {
        this.investmentId = Objects.requireNonNull(investmentId);
        this.description = Objects.requireNonNull(description);
        this.annualExpectedReturn = Objects.requireNonNull(annualExpectedReturn);
    }


    public String investmentId() {
        return investmentId;
    }


    public String description() {
        return description;
    }


    public BigDecimal annualExpectedReturn() {
        return annualExpectedReturn;
    }


    /** RN6: rendimiento anual esperado / 52, en dólares con 2 decimales. */
    public BigDecimal weeklyReturn() {
        return annualExpectedReturn.divide(WEEKS_PER_YEAR, 2, RoundingMode.HALF_EVEN);
    }
}
