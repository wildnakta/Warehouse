```python
!pip install shap
import shap

# XGBoost Model 학습
x, y = shap.datasets.boston()
model = xgboost.XGBRegressor().fit(x, y)

# SHAP를 사용한 모델 예측 설명
explainer = shap.Explainer(model)
shap_values = explainer(x)


# 예측 설명의 시각화1. waterfall plot
shap.plots.waterfall(shap_values[0])
# 변수들의 공헌도 시각화. 예측력을 높여주는 변수는 빨간색, 예측력을 낮추는 변수는 판란색으로 표시


# 예측 설명의 시각화2. force plot
shap.plots.force(shap_values[0])

shap.plots.bar(shap_values)
```
