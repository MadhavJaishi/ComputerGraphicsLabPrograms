#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <GL/glut.h>
int x1, y11, x2, y2, incx = 1, incy = 1, x, y, p;
float m;
void init() {
  gluOrtho2D(0, 500, 0, 500);
}
void plotpoint(int x, int y) {
  glColor3f(1, 0, 0);
  glBegin(GL_POINTS);
  glVertex2i(x, y);
  glEnd();
  glFlush();
}
void LineBres(int x1, int y11, int x2, int y2)
{
  x = x1;
  y = y11;
  int dx = abs(y2 - y11);
  int dy = abs(x2 - x1);
  //Negative Slope
  if (x2 < x1) {
    incx = -1;  
  }
  if (y2 < y11) {
    incy = -1;
  }
  m = dy / dx;
  if (m < 1) {
    plotpoint(x1, y11);
    p = 2 * dy - dx;
    for (int i = 0; i < dx; i++) {
      x = x + incx;
      if (p < 0) {
        p = p + 2 * dy;
        y = y;
      }
      else {
        p = p + 2 * dy - 2 * dx;
        y += incy;
      }
      plotpoint(x, y);
    }
  }
  else {
    plotpoint(x1, y11);
    p = 2 * dx - dy;
    for (int i = 0; i < dy; i++) {
      y = y + incy;
      if (p < 0) {
        p = p + 2 * dx;
        x = x;
      }
      else {
        p = p + 2 * dx - 2 * dy;
        x += incx;
      }
      plotpoint(x, y);
    }
  }
}
//Positive Slope: m < 1, m > 2, m = 1
//Negative Slope: m < 1, m > 2, m = 1
void Display() {
  glClear(GL_COLOR_BUFFER_BIT);
  glClearColor(1, 1, 1, 1);
  LineBres(x1, y11, x2, y2);
  glEnd();
  glFlush();
}
int main(int argc, char **argv) {
  printf("Enter 2 points: ");
  scanf("%d%d%d%d", &x1, &y11, &x2, &y2);
  glutInit(&argc, argv);
  glutInitWindowPosition(50, 50);
  glutInitWindowSize(500, 500);
  glutCreateWindow(".Line.");
  init();
  glutDisplayFunc(Display);
  glutMainLoop();
  return 0;
}
